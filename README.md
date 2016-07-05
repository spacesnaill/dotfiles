# dotfiles
> Setup and sync your Mac system in the quickest way possible.



## Overview
This dotfiles project is a combination of some bash scripts and some dotfiles. The bash scripts automate setup and installation of dev tools, apps, symlinks, and other things. The dotfiles are local configuration files that we're moving to Dropbox in order to sync multiple systems to the same configuration.

### Why?
The hardest part about setting up a new computer is getting your configurations and tools up to par with your old machine. Maybe you're upgrading computers, maybe you're trying to sync multiple workstations, or maybe you want to protect yourself from a future catastrophe. A system like this makes it painless.

### How It Works
It's pretty straightforward. This system:

* Symlinks your bash configurations, Git config and any other configs to Dropbox, allowing all of your machine to sync up to your configuration.
* Automates installation of your dev tools mostly using Homebrew.
* Automates installation of your Mac applications using Homebrew.
* Automates the entire setup and configuration of macOS in seconds.

### Folder Structure
The folder structure of my `~/Dropbox/_config` folder is this repo, plus some stuff not seen in this repo. With the amount of apps that support native Dropbox sync, I'm currently setting those up to sync to Dropbox in `_config/appdata`. I also sync a few additional apps, such as SublimeText.

My `dotfiles` folder includes config dotfiles and scripts.

```shell
_config/
├── README.md
├── appdata
│   ├── 1Password
│   ├── Alfred
│   ├── Sublime
│   ├── TextExpander
│   └── iTerm
└── dotfiles
    ├── bash_aliases
    ├── bash_profile
    ├── bash_prompt
    ├── gitconfig
    ├── mackup.cfg
    ├── scripts
    │   ├── setup-apps
    │   ├── setup-brew
    │   ├── setup-npm
    │   ├── setup-macos
    │   └── symlink
    └── themes
```

### Setup scripts

* [symlink](/dotfiles/scripts/symlink) - Symlinks local config files to your Dropbox config folder.
* [setup-brew](/dotfiles/scripts/setup-brew) - Install and configure packages managed by Homebrew.
* [setup-apps](/dotfiles/scripts/setup-apps) - Install and configure applications managed by Homebrew Cask.
* [setup-npm](/dotfiles/scripts/setup-npm) - Install and configure packages managed by NPM.
* [setup-macos](/dotfiles/scripts/setup-macos) - Set your macOS defaults. Reboot required.



## Initial Setup

Since we're setting up our system to sync to Dropbox, the first thing you want to do on your brand new Mac is [download and install the Dropbox app](https://www.dropbox.com/downloading). Afterwards we'll execute the bash scripts.

### Setup Dropbox for Selective Sync
We don't want to pull down our entire Dropbox yet. So follow these instructions to selectively sync your Mac config file. I use a `_config` in my Dropbox folder to store all of my configuration files.

* Go to Dropbox Preferences
* Select the Account tab
* Select the "Change Settings" button next to "Selective Sync"
* Select only the "_config" folder for fastest syncing
* Wait for sync to finish

### Bash Setup
Now we're ready to run our setup scripts. Open up Terminal then head over to your config folder.

```shell
cd ~/Dropbox/_config/dotfiles/scripts
```
Then run your setup scripts. If this is your first time setting up dotfiles, you'll probably have to run `chmod +x` on your files to make them executable. Otherwise you can just run them as is. I normally run these scripts one by one to ensure things are going smoothly.

```shell
./symlink

./setup-brew

./setup-npm

./setup-apps

./setup-osx
```

## Using Github instead of Dropbox
I use Github as a backup, reference, and place to share this repo. My latest configuration always stays here and I can easily pull down this repo and setup my machine. The benefit of Dropbox is the real time syncing. So when I make edits to my configuration, my other systems are being updated in real time due to the Dropbox. When I'm finished I push my edits to this repo for safe keeping.