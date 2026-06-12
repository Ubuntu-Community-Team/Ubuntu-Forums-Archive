---
title: "Ubiquity and Debian"
date: 2009-04-23
forum: General Help
---

### Post by Isilion on 2009-04-23
hi. i am trying to build my own linux distro, based in debian, and i would like to use Ubiquity as its installer.
but when i add the repos, an then install ubiquity, something goes wrong and the updater starts to uninstall debian packages and to install ubuntu ones. i think its a dependancy problem.
can anyone help me to solve this? all the other programs, except ubiquity, are from debian repos. but i NEED that installer. plz help.

---

### Post by mttza1 on 2010-10-11
hey, im trying to do the same thing...

dont bother with the ubuntu repositories: use [packages.ubuntu.com]("http://packages.ubuntu.com") to get the .deb files (scroll down to the search), , or use launchpad and github to get sources and build a custom .deb file you can also edit most defaults by opening the .deb in archive manager, or by using the source and building a .deb, settings relating to things like, for example, the sideshow (i think thats on a [different package]("http://packages.ubuntu.com/maverick/ubiquity-slideshow-ubuntu") though) or text data... BUT im not 100% sure if [ubiquity]("https://code.launchpad.net/~ubuntu-installer/ubiquity/trunk") will work with debian, and if not, you can either edit the source and build a package (```
dpkg-buildpackage
``` - part of the package dpkg-dev) or use alternative live-installers designed for debian like [Linux Mint's brand new live-installer]("http://github.com/linuxmint/live-installer") (run ```
git clone http://github.com/linuxmint/live-installer.git
``` and then build the package with ```
dpkg-buildpackage
```), or the older BOSS alternative...

i would recommend attempting to use ubiquity and falling back onto linux mint's live-installer. Look it up on youtube if you wanna see it in action ;)

and if you DO get ubiquity to work on debian - please post here saying how

---

