---
title: "Cannot burn DVD-R"
date: 2006-08-01
forum: Desktop Environments
---

### Post by theanswriz42 on 2006-08-01
This seems to be a recent issue so I'm not sure if something changed as per upgrades or what not but here's the issue:

I'm trying to burn a .img file in k3b (also used growisofs with the same results) and am getting the error:

```
root@enceladus:/home/steve# growisofs -dvd-compat -speed=2 -Z /dev/sr0=/home/steve/stuff/torrents/vid/image.img
Executing 'builtin_dd if=/home/steve/stuff/torrents/vid/image.img of=/dev/sr0 obs=32k seek=0'
/dev/sr0: "Current Write Speed" is 1.0x1385KBps.
:-[ WRITE@LBA=0h failed with SK=5h/ASC=30h/ACQ=05h]: Wrong medium type
:-( media is not formatted or unsupported.
:-( write failed: Wrong medium type

```

What is bizarre about this is that the drive I'm using and the DVD-R media hasn't changed from the last time I used k3b to burn an image file so I have no idea what's going on. Any suggestions?

---

### Post by ciscosurfer on 2006-08-01
Are you using Gnome or KDE?

---

### Post by theanswriz42 on 2006-08-02
I've tried in Gnome, KDE, fluxbox, enlightenment, etc. and have the same error. I also have the dvd+-rw package installed and all the relevant packages to burn DVDs.

---

### Post by theanswriz42 on 2006-08-02
Anyone have any ideas?

---

### Post by ciscosurfer on 2006-08-03
Try to burn using CD/DVD Creator in your places menu.  If you get the same error again I would venture to say your CD/DVD drive has failed.

Btw, can you play a CD?

---

