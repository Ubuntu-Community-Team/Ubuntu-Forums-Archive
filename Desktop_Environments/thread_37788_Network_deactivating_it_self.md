---
title: "Network deactivating it self"
date: 2005-05-28
forum: Desktop Environments
---

### Post by pumpkinpatch on 2005-05-28
This is a two parter.

I installed a new hard drive and I can't tell if its working.

After the installation the computer keeps deactivating itself from the network.  

What do I do?

---

### Post by royg1234 on 2005-05-28
re New hard drive.  I never installed a new one (I personally do it in Windows first, so I can do the formatting and stuff).  But type

> sudo fdisk -l 

This lists all of your local disks.  Find your new hard drive, then [mount it](http://ubuntuguide.org/#windows) .

I'm not sure it will list unformatted disks though, sorry, I'm about as n00b as they come.

[--------------------------------------------------------------------]

re Network.  You're not on wireless, are you?  Wireless disconnects itself if it's not pinged for a little while (a few posts on this somewhere).

I hope that sets you in the right direction.

---

### Post by pumpkinpatch on 2005-05-31
Hard drive is working fine now but computer still keeps deactivating itself from the network.

Its not wireless and I can't figure out why.

---

### Post by royg1234 on 2005-05-31
if it makes you feel better, my Windows does this (but not Ubuntu).   :razz:

---

### Post by pumpkinpatch on 2005-05-31
Hard drive is working fine now but computer still keeps deactivating itself from the network.

Its not wireless and I can't figure out why.

---

