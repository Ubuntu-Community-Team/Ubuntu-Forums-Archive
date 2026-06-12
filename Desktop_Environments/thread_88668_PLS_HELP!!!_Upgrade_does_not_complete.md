---
title: "PLS HELP!!! Upgrade does not complete"
date: 2005-11-10
forum: Desktop Environments
---

### Post by duck on 2005-11-10
I attempted to upgrade to Breezy from a terminal but it did not complete correctly. Programs then started to not work so I restarted hoping that would fix the problem. Instead now the GUI does not load and xstart doesnt work. When I try sudo apt-get -f upgrade I get the following error msg:
Unpacking replacement gvlc ...
dpkg: error processing /var/cache/apt/archives/gvlc_0.8.4-svn20050920-3+hal0ubuntu3_i386.deb (--unpack):
trying to overwrite '/usr/share/applications/gvlc.desktop', which is also in package vlc
Errors were encountered while processing:
/var/cache/apt/archives/gvlc_0.8.4-svn20050920-3+hal0ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Then it sends me back to $ prompt.

I initially upgraded using the following:

   1.

      Open up a terminal
   2.

      sudo gedit /etc/apt/sources.list
   3.

      Replace with the following:

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main universe multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main universe multiverse restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

   1.

      sudo apt-get update
   2.

      sudo apt-get dist-upgrade


Any information anyone could offer that might help would be massively appreciated. thanks

---

### Post by etc on 2005-11-10
Remove vlc, then upgrade.
glvc is trying to overwrite what looks like a menu entry, but to keep everything clean I'd just remove vlc, then upgrade, and the install vlc.

I'm not sure about the programs not loading, maybe the upgrade halted in midinstallation because of the vlc issue.

---

### Post by duck on 2005-11-10
thanks for the help. do you know the code to remove vlc as I am somewhat of a linux newb. thanks in advance

---

### Post by duck on 2005-11-10
I tried sudo apt-get remove vlc and no luck. It spat out another error code saying I should try -f install which is the problem in  the first place. Please help

---

### Post by RAOF on 2005-11-10
You could try
```
sudo apt-get --fix-broken dist-upgrade
```
If that doesn't work, you could try
```
sudo dpkg --remove vlc
```
which should remove vlc, and allow you to dist-upgrade normally.

Failing that,
```
sudo dpkg --remove vlc --force-all
```
will **definitely** remove VLC, and ignore any problems encountered on the way, even if they are serious.  This should be a last resort.

---

