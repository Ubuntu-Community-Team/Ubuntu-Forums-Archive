---
title: "Problem with Updates"
date: 2008-11-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by hunterGT on 2008-11-23
This happened on my Win XP - Ubuntu dual boot Inspiron 6000, which is why I decided to put this thread in here. I have no idea what caused this, but this is the first time I've actually tried to tackle it in a long time. Here's a screenshot of the situation:

[IMG]http://picasaweb.google.com/lh/photo/PxkAPsTw2ZgStRsAcAHjEQ[/IMG]
EDIT: Screenshot may not appear, trying new Google Picasa Web Albums...


Every time I try to update now I get this message:

```
W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2_2.6.31.dfsg-2ubuntu1.1_i386.deb
  404 Not Found


W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2-utils_2.6.31.dfsg-2ubuntu1.1_i386.deb
  404 Not Found


W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/libx/libxml2/python-libxml2_2.6.31.dfsg-2ubuntu1.1_i386.deb
  404 Not Found

```

I haven't done much to this machine; I think the only thing I've added was restricted drivers and flash-nonfree. This is the first time I've had a problem with Ubuntu not being able to update.

---

### Post by tm007 on 2008-11-23
Try using any, or all of the fix options in recovery startup when you reach the GRUB boot menu. I believe the filesystem check option in recovery mode is like XP's CheckDisk that runs at the boot-up of XP's sometimes. If I'm right that should help recover some of your missing system files.

BTW... I recommend going to [http://get.adobe.com/flashplayer/?promoid=BUIGP]("http://get.adobe.com/flashplayer/?promoid=BUIGP") and download and install the flashplayer v10. Select the .deb 8.04 in the drop down menu. Flashplayer v10 has best souund and video quality in my opinion.

---

### Post by hunterGT on 2009-01-20
I just deleted the partition that I had Ubuntu on in Windows then installed Ubuntu 8.10, and it cleared the problem. Though I just think this thing is on its way out, it seems to have more and more problems every day and every distribution.

---

