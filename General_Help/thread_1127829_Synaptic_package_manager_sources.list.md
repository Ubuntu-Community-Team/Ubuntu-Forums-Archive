---
title: "Synaptic package manager sources.list"
date: 2009-04-16
forum: General Help
---

### Post by andy71600 on 2009-04-16
Does anyone have the default sources.list file for the synaptics package manager? I made a mistake when trying to add a repository, and cannot figure out what went wrong...

This is the file I am talking about
```
/etc/apt/sources.list
```

---

### Post by jrdonnaruma on 2009-04-16
Here you go, pulled from a freshly booted live-cd in a VM. :-)

```
deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release Candidate amd64 (20090414.2)]/ jaunty main restricted
deb http://archive.ubuntu.com/ubuntu jaunty main restricted
deb-src http://archive.ubuntu.com/ubuntu jaunty main restricted

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu jaunty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu jaunty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
# deb http://archive.ubuntu.com/ubuntu jaunty universe
# deb-src http://archive.ubuntu.com/ubuntu jaunty universe
# deb http://archive.ubuntu.com/ubuntu jaunty-updates universe
# deb-src http://archive.ubuntu.com/ubuntu jaunty-updates universe
# deb http://security.ubuntu.com/ubuntu jaunty-security universe
# deb-src http://security.ubuntu.com/ubuntu jaunty-security universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# deb http://archive.ubuntu.com/ubuntu jaunty multiverse
# deb-src http://archive.ubuntu.com/ubuntu jaunty multiverse
# deb http://archive.ubuntu.com/ubuntu jaunty-updates multiverse
# deb-src http://archive.ubuntu.com/ubuntu jaunty-updates multiverse
# deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
# deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse

```

---

