---
title: "Can not install Xine"
date: 2006-04-14
forum: Desktop Environments
---

### Post by u0014 on 2006-04-14
I am kind of new to this whole Linux business, so there is so much I don't know... I tried intalling Xine and this is what I get: 

u0043@ubuntu:~$ sudo apt-get install xine-ui
Reading package lists... Done
Building dependency tree... Done
Package xine-ui is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xine-ui has no installation candidate

So I am lost, anybody out there could enlighten me?

---

### Post by Ensnared on 2006-04-14
Chances are you need to enable more of the repositories in your /etc/apt/sources.list. If you open this file (with sudo to edit it) you'll see several of the repositories commented out (universe, multiverse, backports, etc). Remove the #-mark to activate them, then save the file. After that, run "sudo apt-get update" and try installing xine-ui again.

---

