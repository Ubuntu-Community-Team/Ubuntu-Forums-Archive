---
title: "XP won't read off NTFS disk written on by Ubuntu"
date: 2008-12-28
forum: General Help
---

### Post by test_test_testing on 2008-12-28
Well basically I installed Ubuntu Intrepid as a Wubi installation to try it out etc., (details are here in a thread about another problem I had - [http://ubuntuforums.org/showthread.php?t=1019853](http://ubuntuforums.org/showthread.php?t=1019853)). I installed the Ubuntu in E:/ and Windows could boot fine with that, however I transferred Ubuntu to its own partition and then wrote to the C drive erasing a line from boot.ini (option to boot from Ubuntu Wubi), and downloading some stuff to the E drive. This is when the problems started as Windows now threw a BSOD whenever I tried to boot (UNMOUNTABLE_BOOT_VOLUME). I ran chkdsk /r from the recovery console, however it says C has an unrecoverable problem. I checked with chkdsk D: /r and chkdsk E: /r, D was fine (I didn't write on it with Ubuntu) however E also had an unrecoverable problem. I have no problem accessing these drives from Ubuntu, so what's going wrong?

Any help would be appreciated.

---

### Post by pastalavista on 2008-12-28
The problem, I believe, is that Windows has locked the drive until it can be repaired. You'll need a Windows recovery disk and run fixboot, fixmbr, repair/restore or whatever it needs as many times as it takes until it shuts down cleanly. You may need to reiinstall Ubuntu again afterwards but possibly not... I didn't except for restoring grub. I had a similar experience over a year ago and this is how I fixed it, but mine wasn't a Wubi install.

---

### Post by test_test_testing on 2008-12-28
Right, fixboot has utterly messed up my system :P. It automatically detected that the filesystem is FAT16, and reported that the boot sector is corrupted, so it overwrote it. Thanks for the help anyway... I am currently writing this from the Ubuntu Live CD (already crashed twice).

I cannot boot from any OS now, gEdit shows that my three partitions have merged into one FAT16 partition with errors on it. When I boot an error says NTLDR is missing. Boot from CD... (or something along those lines). I'm probably gonna reinstall everything then (lucky I backed up just a few days ago). However, does anybody have any ideas on how to recover some of the other files that I might have missed, or recover the boot sector completely before I do this and erase all my programs and customizations? :(

---

### Post by Sef on 2008-12-28
Get [Super GRUB Disk]("http://supergrubdisk.org").

---

### Post by test_test_testing on 2008-12-29
Right, finally managed to successfully run testdisk from a Live CD, and it worked! Reset GRUB, and I can now boot from Ubuntu, however XP still refuses to boot. I'm now back where I started. Help please!

---

