---
title: "Unwanted disks in Places"
date: 2008-05-10
forum: Desktop Environments
---

### Post by Anderuso on 2008-05-10
I have an VT6410 RAID controller, 2 disk attached to it in a mirror (RAID 1). When I install Ubuntu 8.04 I found two items in Places menu to mount this two disks. When I mount one of them and write something to it, data are written only to this particular disk and not to another one (mirror is not working). So I use dmraid to create new mount point for mirror (I use this guide: [http://ubuntuforums.org/archive/index.php/t-2557.html](http://ubuntuforums.org/archive/index.php/t-2557.html)). Now I have new item in Places and when I mount this, writing works fine (data are present on both disks). Mounting previous two items in Places stops working with error: fuse: mount failed: Device or resource busy So my question is, how to remove first two items from Places?

---

### Post by njparton on 2008-05-12
It sounds like you don't have the drivers for that particular controller installed and that it's not supported by the kernel by default.
 
Do drivers for the 2.6 kernel exist on the manufacturers website?  If not you're probably out of luck.

---

