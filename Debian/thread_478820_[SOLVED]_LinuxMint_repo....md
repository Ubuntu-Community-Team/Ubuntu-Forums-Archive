---
title: "[SOLVED] LinuxMint repo..."
date: 2007-06-19
forum: Debian
---

### Post by groggyboy on 2007-06-19
this is a quickie:

i was wondering if anyone could post the LinuxMint Cassandra repo list.  There are a couple things i wanna grab off it for my feisty install (namely, mintMenu and mintdisk).

thanks!
groggyboy

---

### Post by UnbreakableMJ on 2007-06-23
This is my /etc/apt/sources.list on Linux Mint 3.0 Cassandra (Feisty Fawn):

```
## UBUNTU REPOSITORIES
## -------------------
##
## Feisty (Ubuntu 7.04)
deb http://archive.ubuntu.com/ubuntu feisty main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty main restricted universe multiverse
##
## Proposed Updates
deb http://archive.ubuntu.com/ubuntu feisty-proposed main restricted universe multiverse
##
## Bug Fixes
deb http://archive.ubuntu.com/ubuntu feisty-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty-updates main restricted universe multiverse
##
## Security Updates
deb http://security.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
##
## Backports
deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse

                                   
## LINUX MINT REPOSITORIES
## -----------------------
##
## Cassandra (Linux Mint 3.0)
deb http://www.linuxmint.com/repository cassandra/
##
## Romeo (Linux Mint Unstable)
## deb http://www.linuxmint.com/repository romeo/


## OTHER REPOSITORIES
## ------------------
##
## Canonical (RealPlayer10, Opera, DesktopSecure etc...) 
deb http://archive.canonical.com/ubuntu feisty-commercial main
##
## Medibuntu (Codecs and extra applications)
deb http://packages.medibuntu.org/ feisty free non-free

```

Everything is default, except for the Medibuntu repo, because [they have changed the address]("http://linuxmint.com/forum/viewtopic.php?t=3138") since the release of Cassandra.

Peace.

---

### Post by groggyboy on 2007-06-23
thanks for the reply, unbreakableMJ!

i've added the LinuxMint repos to my feisty apt list, but now i have a new problem: the mintconfig package is broken!  here's the output from aptitude:```
The following packages are BROKEN:
  mintconfig 
The following NEW packages will be installed:
  mintdesktop mintmenu 
0 packages upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 75.8kB/365kB of archives. After unpacking 1626kB will be used.
The following packages have unmet dependencies:
  mintconfig: Depends: mintdisk which is a virtual package.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
mintconfig [Not Installed]
mintmenu [Not Installed]

Score is -20052

Accept this solution? [Y/n/q/?] 
```

---

### Post by groggyboy on 2007-06-28
ach, whatever.

i ended up wiping feisty and installing cassandra anyways.  feisty and cassandra are so close to each other that it hardly caused a hiccup in my daily routine.  my home partition transferred flawlessly.

anyone know what program makes the terminal spew out those quotes?  it's neat.

---

### Post by exploder on 2007-06-29
The package that gives you the quotes in the terminal is fortune-mod.

---

### Post by sistemico on 2007-07-11
> **groggyboy said:**
> 
  mintconfig: Depends: mintdisk which is a virtual package.
Resolving dependencies...


I download the mintdisk package browsing Bianca repository:
[http://www.linuxmint.com/repository/bianca/](http://www.linuxmint.com/repository/bianca/)

I installed mintdisk*.deb, then you should use synaptic again and mintmenu would be installed.

(I'm Feisty Fawn user).

It works for me, Good luck!

Ricardo

---

