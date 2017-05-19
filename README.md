# jpartain89.brew-file

| **Travis-CI** |
| ------ |
| [![Build Status](https://travis-ci.org/jpartain89/ansible-brew-file.svg?branch=master)](https://travis-ci.org/jpartain89/ansible-brew-file) |

This makes sure that brew-file is installed and then, if you have a Brewfile already, will run brew file against it.

## Requirements

Requires homebrew to be installed on the target macOS machine.

## Role Variables

Available variables are listed below, and there's only one default variable. (see `defaults/main.yml`) The `brewfile_new_install: yes` is if you've never used brewfile, and/or you want a new BrewFile file.

    brewfile_new_install: yes

The dotfile variable below is for if/where you want to insert the `brew-wrap` function lines, so `brew file` is included when running `brew`. It is not required

    brewfile_brewwrap_dotfile: "~/.bash_profile"

The `brewfile_git_repo` is where you set the github repo that you want your BrewFile to sync with. This will create a new github repo under the `username/repo-name` format. Not required.

    brewfile_git_repo: "jpartain89/Brewfile-MacBook"

The `brewfile_github_password` is for setting the `brewfile_git_repo`, as it needs your github password to create the repo. Only required if setting `brewfile_git_repo`

    brewfile_github_password: "xxyyzz"

## Dependencies

XCode needs to be installed on the target macOS machine:

    xcode-select --install

And then follow the prompts. This will install Apple's `git` binary.

## Example Playbook

  - hosts: all

    roles:
       - { role: jpartain89.ansible-brew-file }

### INFO

The one part that NO ONE has ever fully explained, and took me FOREVER to figure out, was WHERE DO VARIABLES GO?!?

Create a directory at the same level as your main playbook named `group_vars` with a file inside named `all.yml` and the variables in there will apply to all of the called hosts.

## License

GPL-3.0

## Author Information

This role was created in 2016 by [Justin Partain](https://jpcdi.com).
