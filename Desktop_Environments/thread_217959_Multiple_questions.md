---
title: "Multiple questions"
date: 2006-07-17
forum: Desktop Environments
---

### Post by linuxfan128 on 2006-07-17
Here are some questions i am interested in some help with.

1. Hdparm is it worth tweaking? 
   Should i upgrade Hdparm to 6.6?
   Here is my current  hdparm /dev/hda
```
/dev/hda:
 multcount    = 16 (on)
 IO_support   =  3 (32-bit w/sync)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 65535/16/63, sectors = 78165360, start = 0

```
2. How do i upgrade firefox to the latest Firefox beta 2? 
3. I Upgraded the kernel recently but when i reboot in to it x.org crashes . How do i fix this? I am using the nvidia driver that installs with automatix. what i was planning to do is just rerun automatix with new kernel

---

### Post by jpkotta on 2006-07-17
1. I only know about DMA tweaks, so I can't help you there.
2. I use Opera.
3. Yeah, you have to reinstall NVidia drivers every time you update the kernel (maybe not for security updates).  I've never used Automatix, but if they use NVidia's installer, then that should work.  If it doesn't, then use NVidia's installer.  HowTo here: [https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

---

### Post by JerMe on 2006-07-18
1. Can you post the outcome of **sudo hdparm -tT /dev/hda**?

---

