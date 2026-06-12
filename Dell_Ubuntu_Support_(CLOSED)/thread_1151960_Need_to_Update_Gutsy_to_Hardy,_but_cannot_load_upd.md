---
title: "Need to Update Gutsy to Hardy, but cannot load updates first"
date: 2009-05-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mysoda on 2009-05-07
Hi
 
I'm fairly new to Ubuntu (I got Dell Inspiron 1525 last year with 7.10 pre-installed).  Stupidly I didn't upgrade to 8.04 while 7.10 was still supported, so I now need updates to 7.10 before I can upgrade to 8.04 which are no longer available through update/synaptic because the files are gone from the repositories
 
I know about [http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/) but I need walking through this one: 
 
(1) how do I make sure I've got all the updates to 7.10 I need before upgrading the distribution?  How do I even tell which updates I haven't got already?
 
Thanks if you can help!
 
mysoda:)

---

### Post by coffeeaddict22 on 2009-05-07
Hi,
The easiest way about it would be to reinstall; download an .iso and cut a CD/ create a USB startup disc.

---

### Post by snowpine on 2009-05-07
Enter the following terminal command:

```
gksu gedit /etc/apt/sources.list
```

Change all instances of 'gutsy' to 'hardy'. Save and quit.

Then,

```
sudo apt-get update
sudo apt-get dist-upgrade
```

I think that might work; it works in Debian. :)

---

### Post by mysoda on 2009-05-08
Hi, thanks for your replies :) - I'm a bit confused still :( and I thought about it some more and wondered if I could get all the updates for 7.10 before I upgrade to 8.04 by changing the sources.list to point to their archive location at old-releases.ubuntu.com?  If so, can you tell me what exactly should I change it to?

**[COLOR=DarkRed]snowpine[/COLOR]** - can I ask, would your solution achieve the same as if I had got the updates to Gutsy (before its EOL) using the Update Manager GUI?  I think my basic problem is that while I can use the upgrade button to automatically get Hardy, all the guidance I've read says I need to check for and install all the updates for my exisitng distribution (gutsy) before doing the upgrade (to hardy).  These are what I'm missing because Gutsy went EOL.
(also, what's gksu?)

**[COLOR=DarkRed]coffeeaddict22[/COLOR]** - if I go for a clean installation of 8.04, can you tell me where to get the proper dell iso from?

This is my current sources.list

```
deb http://archive.ubuntu.com/ubuntu gutsy main restricted universe
deb-src http://archive.ubuntu.com/ubuntu gutsy main restricted universe

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://archive.ubuntu.com/ubuntu gutsy universe
# deb-src http://archive.ubuntu.com/ubuntu gutsy universe

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted universe

## deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
deb http://ppa.launchpad.net/dell-team/ubuntu gutsy main
deb http://archive.ubuntu.com/ubuntu gutsy-updates restricted main universe
deb-src http://archive.ubuntu.com/ubuntu gutsy-updates restricted main universe
deb-src http://ppa.launchpad.net/dell-team/ubuntu gutsy main
```:confused:

---

### Post by snowpine on 2009-05-08
My advice is, don't worry about upgrading your Gutsy first, because all of the packages are going to be replaced with newer versions anyways when you upgrade to Hardy. Simply change your current sources.list so that all the gutsy's are hardy's and don't worry about old-archives.

However, I will admit that I have never been in your exact situation before, so take my advice with a grain of salt. :)

'gksu' is the graphical equivalent of sudo. You should use sudo for terminal commands (like sudo apt-get update) and gksu for commands that pop open in a new window (like gksu gedit). If you forget and just use sudo, it is not the end of the world, but it is a good habit to learn the difference.

---

