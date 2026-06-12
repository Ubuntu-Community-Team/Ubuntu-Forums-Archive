---
title: "Any way to install alien offline?"
date: 2006-04-23
forum: Desktop Environments
---

### Post by Jason7fd on 2006-04-23
I wanted to convert my modem driver rpm to deb using alien,but I don't have usable modem for ubuntu now.Can someone please guide me how to install alien offline?

---

### Post by aysiu on 2006-04-23
Ah, Ubuntu without internet... it's a pain.

Go to [http://archive.ubuntu.com/ubuntu/pool/](http://archive.ubuntu.com/ubuntu/pool/) and find these .deb files: ```
alien debhelper html2text libbeecrypt6 libneon25 librpm4 libsqlite3-0 rpm
``` download them from wherever you have internet and then copy them to your desktop in Ubuntu.

Then, in Ubuntu, go to Applications > Accessories > Terminal and type ```
cd ~/Desktop
sudo dpkg -i *.deb
``` You should now have *alien* installed.

---

### Post by az on 2006-04-23
I thought alien was on the breezy cd...

---

### Post by Jason7fd on 2006-04-23
[QUOTE=aysiu]Ah, Ubuntu without internet... it's a pain.

Go to [http://archive.ubuntu.com/ubuntu/pool/](http://archive.ubuntu.com/ubuntu/pool/) and find these .deb files: ```
alien debhelper html2text libbeecrypt6 libneon25 librpm4 libsqlite3-0 rpm
``` download them from wherever you have internet and then copy them to your desktop in Ubuntu.

Then, in Ubuntu, go to Applications > Accessories > Terminal and type ```
cd ~/Desktop
sudo dpkg -i *.deb
``` You should now have *alien* installed.[/QUOTE]
Thanks for that.I have another question,can i get build-essential from here [http://packages.debian.org/stable/devel/build-essential](http://packages.debian.org/stable/devel/build-essential) and install it to Ubuntu?

---

### Post by jrib on 2006-04-23
build-essential is definitely on the cd.  Just put the cd in your drive and make sure you have the cd-rom repository enabled in synaptic (check settings > repos, if it's not there go to edit > add cdrom repo)

---

