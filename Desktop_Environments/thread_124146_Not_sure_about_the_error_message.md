---
title: "Not sure about the error message"
date: 2006-01-31
forum: Desktop Environments
---

### Post by jrutl on 2006-01-31
When using Synaptic Package Manager to install new applications  I continually get the following error message in terminal screen.  

[COLOR="Navy"]W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe/Packages Packages (/var/lib/apt/lists/us.archive.ubuntu.com_dists_breezy_universe_Packages_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe/(/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) Packages (/var/lib/apt/lists/us.archive.ubuntu.com_dists_breezy_universe_(_var_lib_apt_lists_us.archive.ubuntu.com%5fubuntu%5fdists%5fbreezy%5funiverse%5fbinary- - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe/breezy-updates Packages (/var/lib/apt/lists/us.archive.ubuntu.com_dists_breezy_universe_breezy-updates_binary-i386_Packages) - stat (2 No such file or directory)
[/COLOR]
I am new to Ubuntu and I not sure why this error is be generated.  Any help will be appreciated.  Thanks

John :confused:

---

### Post by Gcool on 2006-01-31
Take a look at your /etc/apt/sources.list file. It should be something like this:

```
deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team

deb http://archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy universe multiverse

## Security Updates
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security universe multiverse

## official backports
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe
```

---

### Post by jrutl on 2006-02-01
Gcool,

Thanks for the help, I changed the sources.list base on your suggestion and installing additional apps was became an error free process.  I will study the current sources.list and compare it to the now sources.list.old to understand the changes.  Thanks again

jrutl


[QUOTE=Gcool]Take a look at your /etc/apt/sources.list file. It should be something like this:

```
deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team

deb http://archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy universe multiverse

## Security Updates
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security universe multiverse

## official backports
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe
```[/QUOTE]

---

### Post by Gcool on 2006-02-01
You're welcome. Have fun exploring ubuntu :)

---

