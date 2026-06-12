---
title: "Reconstuctor - libbogl-dev has no installation candidate"
date: 2009-03-15
forum: General Help
---

### Post by lowester on 2009-03-15
Hello all.

I'm having probs with reconstructor installation. When i try to install the dependacies using

sudo apt-get install squashfs-tools make gcc mkisofs rsync libbogl-dev libusplash-dev gpg dpkg-dev fakeroot apt-utils python python-gtk2 python-glade2

i get the following error

"Package libbogl-dev has no installation candidate"


I've downloaded - libbogl-dev_0.1.18-1.4ubuntu2_amd64.deb and when i try to insatll that I get another error message-

"Dependancy error is not satifiable: libbogl0


I have also download the deb file for libbogl0 - libbogl0_0.1.18-2_amd64.deb

This installs fine, but when I go back and try to install libbogl-dev I get another dependancy not satisfiable pointing to libbogl0.


Would really appreciate some help here as I'm going around in circles with this.


Running - Intrepid 8.10 amd64 2.6.27.11

---

### Post by LegendofTom on 2009-03-15
It looks like you are running 64 bit, and that could be a problem.  I'm guessing your depency is somewhere other than where it is looking.

---

### Post by lowester on 2009-03-15
thnks for reply

yeah i'm running 64bit, have got 32bit libs tho

thing is, I had it installed and working earlier on  but for wahtever reason the app became unresponsive so i uninstalled thginking a quick re-install would do the trick but ????

---

### Post by lowester on 2009-03-15
Finally goT it working by running

sudo apt-get install squashfs-tools make gcc mkisofs rsync libbogl-dev libusplash-dev gpg dpkg-dev fakeroot apt-utils python python-gtk2 python-glade2

For some reason my sources list was called sources.list.orig. renamed it to sources.List and then 'apt-get update' and then ran the reconstructor deb and all is ok

---

