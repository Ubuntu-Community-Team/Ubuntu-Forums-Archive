---
title: "cp'ing zero-length files to USB disk?"
date: 2006-04-03
forum: Desktop Environments
---

### Post by McLogic on 2006-04-03
I have a problem with my USB disk -- a 128mb iRiver mp3/ogg player. It mounts as a USB mass storage device, no player management software needed. 

I CAN write to and delete off the disk fine, while it is connected. After I disconnect the player/disk it says "no files". I get zero-length files when I disconnect and reconnect the drive. 

When I first "cp" the files, they say they are the right size. I can open them just fine.  If I use Nautilus and navigate into, and then out of the copied folders, I come up to the parent folder of the files that I copied onto the disk.  If I unplug the disk and plug it back in, the documents are of zero length. 


I think that cp is making some kind of link. This idea is supported by the short time "cp" takes to copy the files (much too fast). :mad: It worked fine under 5.04, but it is not working under 5.10. It happens the same on a nforce desktop and a Intel 855 laptop -- WTF?  :?

---

### Post by daftspaniel on 2006-04-04
Hi McLogic,

I have a similar problem though sometimes the copy process just hangs on larger files :( 

Also I get some errors when I shutdown Ubuntu 5.10 - I don't have them to hand but they look like low level fs errors (blocks). Ubuntu has created a folder and moved files so has some level of access.

Thanks,
Davy M.

---

