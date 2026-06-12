---
title: "help with nvidia driver and virtualbox on jaunty"
date: 2009-05-09
forum: General Help
---

### Post by mosaic2s on 2009-05-09
have installed jaunty - fresh. working like a charm.

have not yet resolved nvidia display issue.
xp hangs while loading in vbox. is it related to nvidia display issue?

---

### Post by bodhi.zazen on 2009-05-09
Hard to say, perhaps.

What is wrong with the nvidia driver and what happens when virtualbox hangs ?

---

### Post by mosaic2s on 2009-05-10
using the following driver.
173.14.16

when i boot into jaunty, the resolution is 800x 600.

after opening the nvidia x driver setting menu, i get 1280x 1024 resolution. At this stage  
the xorg.conf does not get updated by the nvidia-driver menu.

I have tried pasting the settings myself in xorg.conf. it does not work. am now trying other posts on the nvidia drivers. will keep you posted.

The virtualbox loads alright. I took the xp.vdi from 8.04 and have attached it to the current vbox installation in jaunty. in hardy, nvidia works fine. so vdi is set for 1280 x 1024 resolution. 

no message is posted either by vbox or xp while booting normally. it just hangs. on safe booting, xp hangs at mup.sys.

let me see if i can resolve the monitor resolution. and then post again on this.

---

### Post by mosaic2s on 2009-07-11
for last 3 months have tried many potions for setting jaunty with nvidia drivers. no success.

am using same system with hardy and nvidia driver - no problem. works perfectly. see screen shot for driver info.

jaunty on the same system - before booting - gives an error - i can not save this text in any file  - so i took a picture at this point and have attached to the computer.

any suggestions?

---

### Post by 3rdalbum on 2009-07-11
It's extremely unlikely that the Nvidia driver is causing a problem with a Windows XP guest.

Windows cannot even see your Nvidia graphics card - it sees a generic video device that Virtualbox provides for it. Same with your sound card, networking devices etc.

There must be some other problem.

---

### Post by chipppy on 2009-07-11
With your screen dump can you show the X server information please

Also can you see if you can get a diferrent driver version
System ==> Administration ==> Hardware Drivers

Try an updated version or possible an older version
I know it sound silly but I found that one of my older puters graphics card works better with the 95 driver then the 170 driver

Cheers
chipppy

---

### Post by mosaic2s on 2009-08-05
i am sticking with 8.04 - the LTS version. it is stable and allows me to work.

have removed 9.04 from system.

---

