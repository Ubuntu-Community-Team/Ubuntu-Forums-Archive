---
title: "ubuntu running slow"
date: 2004-12-16
forum: Desktop Environments
---

### Post by bvr on 2004-12-16
This didnt come as a big surprise to me seeing how im using a 333mhz p2 laptop with 64mb of ram, but my question is if it is possible to turn off some graphical features or other things thats really not that useful to the common newbie. 
   I really hope to hear from someone regarding this issue since its virtually impossible for me to do anything with the computer in it's current state, memory usage is constantly at 100%.

---

### Post by jdong on 2004-12-16
Well, that's definitely not enough RAM if you want to run GNOME...

I'd recommend a switch to XFCE (a lighter, gtk+ based desktop). I have version 4.2 RC2 backported to Warty, but it's currently in the testing repository. I'll have it in the stable repository this weekend, if all goes well! Currently, it works and I doubt much is going to be changed before I bump it up....

Stuff to put in /etc/apt/sources.list:

STABLE Backports:
deb [http://ubuntu-bp.sourceforge.net/ubuntu](http://ubuntu-bp.sourceforge.net/ubuntu) warty-backports main universe

TESTING Backports:
deb [http://ubuntu-bp.sourceforge.net/ubuntu](http://ubuntu-bp.sourceforge.net/ubuntu) warty-backports-staging main universe

---

### Post by jdong on 2004-12-16
Just a note: It's note the CPU that's slow in your configuration -- it's the RAM. Do try to get more RAM in that box -- I have a 266 MHZ laptop with 128MB RAM running Ubuntu + XFCE, and it is wonderful and perky.

---

### Post by jodef on 2004-12-19
From synaptic what are the mandatory files necessary in order to run a basic XFCE.

---

### Post by jbennet on 2006-11-07
xubuntu-desktop

---

