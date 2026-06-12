---
title: "Intel Pro Share WebCam (spca50x) not working"
date: 2009-05-04
forum: General Help
---

### Post by soule on 2009-05-04
Hello,

 I have a trusty 10-year old webcam that still works. Oh, and here is the output of lsusb:
> Bus 002 Device 002: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 002: ID 03f0:0b0c Hewlett-Packard 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0ace:1211 ZyDAS 802.11b/g USB2 WiFi
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 0733:0430 ViewQuest Technologies, Inc. Intel Pro Share WebCam
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


 It is a Intel Pro Share WebCam (spca50x) and i have tried to view it under gqcam, which displays the following if i execute the command "sudo gqcam"

/dev/video: No such file or directory 

I then tried ls /dev/video* , which returned

/dev/video0  /dev/video1  /dev/video2

I then executed the command  sudo camorama  , which displayed a whole lot of irrelevant issues with my theme that were unimportant, than opened the window and claimed "Unable to capture image." in an error box and if i hit ok it would exit.

Please assist?


-soule

---

### Post by elord on 2010-08-22
I got same problem with this one.. after upgrading from Hardy to Lucid i can't use my CAM for my skype..I search the entire possible solution but i got nothing.. Please if anyone here have an idea how solve this problem please help us..

---

### Post by elord on 2010-08-22
Thanks GOD i solve it already for several hours searching in the net for possible solution now i can use my CAM ..

install Chesse and libcheese-gtk-dev

---

### Post by chyapay on 2011-04-08
No! Installing cheese and its dev headers does not help at all. The camera is usable in cheese application, but not in Skype nor any other software, which depends on /dev/video. It seems that cheese utilizes its own user-space libraries to handle the webcam, as it has all the necessary controls (brightness/contrast/saturation/effects etc) , which are not entirely supported by linux driver module.

Someone please help.

---

### Post by no2498 on 2011-04-08
open a terminal type dmesg click enter


also find and install xawtv
try the cam in xawtv
its in the repose

---

