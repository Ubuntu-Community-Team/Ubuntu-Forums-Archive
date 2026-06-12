---
title: "unable to enable desktop effects"
date: 2009-04-29
forum: General Help
---

### Post by underdog512 on 2009-04-29
I just did a fresh install of Ubuntu 9.04 with the ext4 filesystem on my dell studio 15 laptop.  Everything is working great so far except....

I am unable to enable desktop effects.  When I go to System -> Preferences -> Appearance -> Visual Effects tab, I select Normal and I get a message saying "searching for drivers" for a few seconds, then it comes up a says "Desktop effects could not be enabled."  

This worked on 8.04 without any problem.

---

### Post by freonchill on 2009-04-29
do you want desktop effects or compiz?

---

### Post by underdog512 on 2009-04-29
Whatever the default is in Ubuntu.  I am guessing that would be Desktop Effects.

---

### Post by change_mode on 2009-04-29
Check 

Administration -> Hardware Drivers

You have to install the proprietary graphics drivers first.

---

### Post by underdog512 on 2009-04-29
the only thing listed in there is my WiFi Card and it is enabled.

---

### Post by cms2337 on 2009-04-30
I have the exact same issue... it is a carbon copy

---

### Post by castlefox on 2009-04-30
I have an inter-graded Intel card.  I am having the exact same issues.  

I think there were some regressions with the Intel stuff with 9.04

---

### Post by underdog512 on 2009-04-30
Apparently drivers for the intel 965/960 cards has been blacklisted because of a freezing issue.  

According to this bug report, they are really close to have the issue fixed.

[https://bugs.launchpad.net/ubuntu/jaunty/+source/xserver-xorg-video-intel/+bug/359392](https://bugs.launchpad.net/ubuntu/jaunty/+source/xserver-xorg-video-intel/+bug/359392)

---

### Post by wii552 on 2009-09-06
i am having the exact same problem....could i install the drivers off my install disk?(or flash drive, as i use a netbook....)

---

