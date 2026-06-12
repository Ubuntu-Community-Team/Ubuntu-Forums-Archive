---
title: "Please Insert Disc Labeled Hoary"
date: 2005-09-17
forum: Desktop Environments
---

### Post by asimon623 on 2005-09-17
A lot of times when I'm trying to install something from synaptic or apt-get, it asks for a disc. Can I rip the disc to the computer somehow and have syanptic look to that directory?

---

### Post by Leif on 2005-09-17
You need to remove it from your source. do sudo gedit /etc/apt/sources.list, find the line towards the top with the cdrom mentioned in it :

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

, put a # in front of it

#deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

, save, sudo apt-get update and the message will go away.

---

### Post by az on 2005-09-17
[QUOTE=asimon623]A lot of times when I'm trying to install something from synaptic or apt-get, it asks for a disc. Can I rip the disc to the computer somehow and have syanptic look to that directory?[/QUOTE]

The installation CD contains a few more packages than what is used in the install.  The first stage of installation installs a base system that can then install the rest of the Ubuntu Os By itself.

Breezy's first stage of installation will install even less than the presious versions.  All that will be installed at that point is what you need to boot and run dpkg.

So, the packages are copied from the cd to the /var/cache/apt/archive/ directory.   You probably played around with synaptic and told it to clean out the cache.  

The archive-copier package is in the installer.  I do not know of a similar package that is in the debian package tools, but you can always just mount your cd and copy all the .deb files recursively into /var/cache/apt/archive/

Alternatively, do as stated above and just use the online repositories.

---

### Post by digeratess on 2007-07-18
Nearly 2 years later, and this post helped me out with the same annoyance on a Feisty server. Thanks community and thanks Canonical for providing deep archives and a great search feature. The great community and great tools for interacting with it are a large part of why Ubuntu rocks.

---

### Post by john-woods on 2007-07-24
Like digeratess this post just helped me out with Feisty too, thanks Leif and az!

---

### Post by manefraim on 2007-08-13
Word up. Me two. Just helped. Thanks!

---

### Post by Gremlinzzz on 2007-08-13
You ubuntu started in 2004-09-16 what was the name before ubuntu?
here's hoary disk
[http://distrowatch.com/index.php?distribution=ubuntu](http://distrowatch.com/index.php?distribution=ubuntu)

---

