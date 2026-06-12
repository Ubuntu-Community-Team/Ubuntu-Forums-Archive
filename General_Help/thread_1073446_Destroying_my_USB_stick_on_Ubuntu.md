---
title: "Destroying my USB stick on Ubuntu"
date: 2009-02-18
forum: General Help
---

### Post by grindedrick on 2009-02-18
Hello once again,

I have been mounting my usb stick for a long time now without problems. Yesterday I accidentally mis-spelled the device to mount. I then ran the mount command again with the proper device my USB stick was recognized as. Well it kept saying read-only file system. So I unmounted and remounted with -rw. No problem. Well when I ran my usual cp command to put new data on it, it started blinking crazy and wouldn't stop. I couldn't unmount it either. I tried shutting down but couldn't because of IO operations being performed on the stick. After about 5 minutes waiting I gave up and pulled the stick.

It turns out the cp operation left a bunch of machine code on there which I couldn't remove. I then reformatted to FAT32 and tried again. It seems every time I put data on the stick from Linux it destroys it. It still works fine under Windows. Any idea what's going on? I've been using it for almost a year without any problems until now.

---

### Post by grindedrick on 2009-02-18
[Resolved]:
I ran mkfs.vfat /dev/*usb-device-label* reformatting it on ubuntu.

Seems to work fine now. 
For whatever reason the program I used to format it on Windows must not have been making it compatible with Linux.

---

