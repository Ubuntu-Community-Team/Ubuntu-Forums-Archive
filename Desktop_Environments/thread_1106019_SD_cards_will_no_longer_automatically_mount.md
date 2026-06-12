---
title: "SD cards will no longer automatically mount"
date: 2009-03-25
forum: Desktop Environments
---

### Post by KarenAB on 2009-03-25
Hi,

I am new to the forum and somewhat new to Linux.  I recently upgraded from a 7.? version (Feisty Fawn) to 8.04 LTS. I use EXT2 formated SD cards to transfer files to an external device and have always been able to insert them in to a USB - MMC card adapter and Ubuntu would always automatically mount the SD card and show it on the desktop. When I initially installed 8.04 this still worked however shortly after SD cards would no longer mount automatically and I have to go in with Terminal and manually find them in the "dev" directory and mount them. the "df" command don't seem to work that well either.  I am not sure if this is normal but the device name changes from SDD1 to SDF1 then to SDE1 and back to SDD1 different times with new insertions but not always. I do try to unmount them before removing but could have missed a couple of times.

I also have an external USB to HardDrive adapter with a 20g drive (Ext2 or Ext3 I forget) and used it backed up most of my files from the old system but now 8.04 won't find and mount this device either. I see 3 devices that appear to be it but am having trouble mounting it.

I have been using e2fsck, and fsck.ext2 and fsck.ext3 to try to help identify the devices as well.

Hope the post was to the correct place and not to long.

Thanks very much for any help on how to get it to recognize and auto mount once again!!

Kind regards,

Karen

---

### Post by KarenAB on 2009-03-25
It seems I may have it almost working as before.  I just noticed that it does show up under "Places" when I plug devices in and was able to retrieve the data backed up from my old system.:P

I am still a little confused as to why I could not see it mounted when I looked in /media/  previously.

Any insight as to what may have been the problem if there was one other than me would still be appreciated!

Thanks Much and sorry if I got to anxious to ask for help!

Kind regards,

Karen

---

