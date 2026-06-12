---
title: "apt-get help"
date: 2005-02-10
forum: Desktop Environments
---

### Post by DanVarga on 2005-02-10
Hi, sorry if this has been posted before.  I am new to ubuntu and apt-get, I was wondering if there was a way to see a list of all of the available packages.  I am currently trying to get gtk2 and glib updated and I can't figure out how to do this.  Thanks in advance

---

### Post by rosslaird on 2005-02-10
Actually, there are several ways (at least four that I can think of) of doing what you want. That's the advantage and disadvntage of Linux, depending on how you look at it.

Try Synaptic (Desktop/Adminstration/Synaptic).
Search for the packages you want, or if they are already installed (and it sounds like they might be), just click on "Mark All Upgrades" then "Apply".

You can do exactly the same thing from the command line (it will show you more information, and it will be faster)

sudo apt-get update
sudo apt-get upgrade

(Or "sudo apt-get dist-upgrade" after the update, which is a more comprehensive way to upgrade packages).

Hope this helps. Package management is one of the greatest things about Ubuntu and Debian (upon which Ubuntu is based). The constant upgrades and enhancements can be addictive!

---

### Post by DanVarga on 2005-02-10
Ya, I have tried the Synaptic Package Manager and it shows the packages but wont allow me to upgrade to the latest version.  I know with like emerge on Gentoo it always had the latest versions.  apt-get doesn't seem to have this.  Is there any way I can see every package available to me through apt-get?  I really am just trying to get xine working for dvd playback and to have the ability to compile my own programs that use gtk2

---

### Post by rosslaird on 2005-02-10
If apt won't allow you to upgrade, then there's a version conflict. It will always give you the most recent version for your current configuration (just like portage, on Gentoo).

What does apt say when you try to upgrade? If there's an issue, it will tell you. Post the apt-get output here if you like.

To compile gtk programs (like xfce) you need things a few things. This is (maybe) a full list (others will know more -- I am not a programmer):

gcc
g++
libgtk2.0-dev
libice-dev
libsm-dev
libdbh1.0-dev
a2ps
libxml2-dev
libxpm-dev
libvte-dev
libncurses5-dev
dbus-1-dev
dbus-glib-1-dev
bin86
build-essential
libncurses-dev

Xine should work straight away (apt-get xine or apt-get xine-ui). I think, however that there is an extra package you need for dvd playback:

libdvdcss2

You can get the latest versions of all of the above through synaptic or apt-get (on Hoary, anyway):

apt-get libdvdcss2

That's it.
Am I missing some essential detail?


Ross

---

### Post by DanVarga on 2005-02-10
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate

The error above is one I get frequently.  I am trying to get gtk+ 2.6 installed.  It only downloads and installs 2.4 from apt-get is there something I am missing?

---

### Post by rosslaird on 2005-02-10
I hate Hate HATE that message. Drives me crazy. Usually it means you need more sources. libdvdcss2 is available from [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main (I just got it from there). Here's my sources list, which includes the sources you're looking for:


```
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Alpha i386 Binary-1 (20050204)]/ unstable main restricted


deb http://archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb http://archive.ubuntu.com/ubuntu hoary-updates main restricted
# deb-src http://archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu hoary universe
deb-src http://archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

# Other sources #

deb http://archive.ubuntu.com/ubuntu/ warty multiverse
deb-src http://archive.ubuntu.com/ubuntu/ warty multiverse

deb ftp://ftp.nerim.net/debian-marillat/ stable main
deb ftp://ftp.nerim.net/debian-marillat/ unstable main
deb ftp://ftp.nerim.net/debian-marillat/ testing main

# os-works.com (xfce) #

deb http://www.os-works.com/debian testing main
deb-src http://www.os-works.com/debian testing main

```

(I'am assuming you're running Hoary. If not, be cautious about adding the above source en masse.)

Change your /etc/apt/sources.list to include all of the above sources, then run:

apt-get update

Then try again. Let me know what happens.

Ross

---

### Post by DanVarga on 2005-02-10
That did the trick.  Thanks a whole lot! :)

---

