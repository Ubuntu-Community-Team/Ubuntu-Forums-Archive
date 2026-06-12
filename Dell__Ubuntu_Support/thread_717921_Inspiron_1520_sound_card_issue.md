---
title: "Inspiron 1520 sound card issue"
date: 2008-03-07
forum: Dell  Ubuntu Support
---

### Post by brysono on 2008-03-07
I've been through quite a few fixes for the sound card issue and none have worked. The most common fix people have suggested is 
sudo apt-get install linux-backports-modules-generic

However when I do that i get the following:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package linux-backports-modules-generic

So How do I fix this problem or is there another way that isn't too complicated to fix the sound card? Keep in mind I'm a beginner when you reply with solutions. Any help would be much appreciated. Thanks!

---

### Post by kryth on 2008-03-09
try this
go to system>>admin>>software source
go to update tab
check the box that says Unsupported update(backports)
close it, reload
then try 
sudo apt-get install linux-backports-modules-generic

---

### Post by superprash2003 on 2008-03-10
hope this helps [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

