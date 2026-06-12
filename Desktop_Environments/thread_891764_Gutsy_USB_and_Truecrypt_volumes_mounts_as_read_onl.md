---
title: "Gutsy: USB and Truecrypt volumes mounts as read only"
date: 2008-08-16
forum: Desktop Environments
---

### Post by antiOST on 2008-08-16
Hi

When I mount my USB stick it mounts as read only. This started recently before that it mounted perfectly as read/write.
I just experienced the same behaviour with my truecrypt volumes as well.

Please advise, it's driving me insane that I have to boot my XP to copy files to my USB.

-Kim

Output for uname -a:
Linux Arrakis 2.6.22-15-generic #1 SMP Fri Jul 11 19:25:33 UTC 2008 i686 GNU/Linux

---

### Post by antiOST on 2008-08-27
ANYONE..... somebody must be able to give som advice, it really really sucks to have to boot up in windows XP to write to my truecrypt og usb devices.. 

:-(

-Kim

---

### Post by antiOST on 2008-08-27
F**k it.. I booted up my XP, deleted all my files on the usb-stick, guess what some files where corrupted and could not be deleted..

well I was in a bad mood so I used the F-word once more and reformatted the usb-stick with FAT32 and suddently all my usb problems with ubuntu was gone.

Well I was ready to do the same with my truecrypt folder, so I copied (I wasn't that mad that I wanted to lose 50GB in files) the files to my windows drive and again there were som corrupted files. 
I couldn't just format this drive with all my files, so I ran a chkdsk -F and answered Yes to correct errors and now my truecrypt folder is read/write again.

I guess my evening went well eventually

:-)
Kim

---

