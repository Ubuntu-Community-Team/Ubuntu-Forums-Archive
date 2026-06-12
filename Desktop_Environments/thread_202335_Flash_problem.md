---
title: "Flash problem"
date: 2006-06-23
forum: Desktop Environments
---

### Post by Mike_N on 2006-06-23
So i ran... sudo apt-get install flashplugin-nonfree

And got this... Couldn't find package flashplugin-nonfree

I had no problrms with this before, any ideas?

Thanks, Mike

---

### Post by degel3030 on 2006-06-23
you probably need to un-comment or add repositories /etc/apt/source.list

i think thats how it goes, i know theres some info at the wiki page

---

### Post by Winblowz on 2006-06-23
Replace everything in your /etc/apt/sources.list with the following...
```
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.freecontrib.org/ubuntu/plf dapper free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf dapper free non-free 

```
then, do
```
sudo aptitude update
```

---

### Post by sldavid on 2006-06-23
I had the same problem you did with flash on Ubuntu but was able to successfully install flash in Kubuntu. I imagine this would work in Ubuntu as well.

1. Download the FlashPlayer plugin from the Mozilla website add-ons section [https://addons.mozilla.org/firefox/plugins/](https://addons.mozilla.org/firefox/plugins/).

2. Make sure you download the version for Linux.

3. Extract the downloaded file and take a look at the readme for install directions. Here's the section you're insterested in:

Installation
------------
To install the Plug-in Player for Linux via an install script, follow these directions:

- This installer is script-based and cannot be run from a GUI.

- Uncompress install_flash_player_7_linux.tar.gz.  A directory called install_flash_player_7_linux is created.  Navigate to this directory.

- From the command line, type ./flashplayer-installer to run the installer.  The installer will instruct you to shut down your browser(s).

- Once the installation is complete, the plug-in will be installed in your Mozilla browser.  To verify, choose Help > About Plug-ins from the browser's menu.

4. Viola. Flash should now be working.

---

