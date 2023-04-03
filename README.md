# Ansible Role Homebrew

## What it does

This Ansible role installs Homebrew on macOS, configures packages, taps, and cask apps according to supplied variables.

## Prerequisites

### Install Xcode Command Line Tools

First install Xcode 

```
xcode-select --install
```

## Install Ansible

```
export PATH="$HOME/Library/Python/3.8/bin:/opt/homebrew/bin:$PATH"
sudo pip3 install --upgrade pip
pip install ansible
```

### Create roles directory

```
mkdir -p $USER/Projects/ansible/roles
cd $USER/Projects/ansible
```

```
cat > ansible.cfg <<EOF
[defaults]
inventory # localhost
EOF
```

```
cat > localhost <<EOF
[localhost]
127.0.0.1  ansible_connection #local
EOF
```

### Clone the repository

```
git clone https://github.com/mantoso/ansible-role-homebrew roles/ansible-role-homebrew
```

### Create Playbook

```
cp roles/ansible-role-homebrew/macos-workstation-example.yml macos-workstation.yml
```

Or if you are ok with the example playbook (you shouldn't be), create a symlink to it:

```
ln -s $(pwd)/roles/ansible-role-homebrew/macos-workstation-example.yml $(pwd)/macos-workstation.yml
```

### Run ansible-playbook

```
ansible-playbook --ask-become-pass macos-workstation.yml
```
