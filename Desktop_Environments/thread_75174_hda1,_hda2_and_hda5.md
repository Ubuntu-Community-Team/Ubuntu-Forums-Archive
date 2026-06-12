---
title: "hda1, hda2 and hda5"
date: 2005-10-13
forum: Desktop Environments
---

### Post by MuRRe on 2005-10-13
Just installed 5.10 AMD64. In the filesystem (where i can go to home desktop and so on) I have three hda as stated in the title.
Are these my windows partitions?
Because hda1 is like the Backup system for my latptop,
hda2 is my windows Xp partition and hda5 is my NTFS partition where i store my files. I dont want hda1 and hda2 to show because there are nothing i need for Ubuntu. Altough i want hda5 to avaliable. How do i do this?

255 huvuden, 63 sektorer/sp&#229;r, 12161 cylindrar
Enheter = cylindrar av 16065 &#215; 512 = 8225280 byte

    Enhet Start     B&#246;rjan        Slut     Block    Id  System
/dev/hda1               1         294     2361523+  12  Compaq-diagnostik
/dev/hda2   *         295        1569    10241437+   c  W95 FAT32 (LBA)
/dev/hda3            2543       12160    77256585    f  W95 Ut&#246;kad (LBA)
/dev/hda4            1570        2542     7815622+  83  Linux
/dev/hda5            4120       12160    64589301    7  HPFS/NTFS
/dev/hda6            3877        4119     1951866   82  Linux v&#228;xling / Solaris
/dev/hda7            2543        3875    10707259+  83  Linux

Sorry for the explation being in Swedish...:)

---

### Post by linbetwin on 2005-10-13
Unmount the partitions you don't need. Open a terminal and write:

[COLOR=Indigo]sudo gedit /etc/fstab[/COLOR]

Enter password when prompted. The fstab file will open in Gedit. Look for the lines that start with [COLOR=Indigo]/dev/hda1[/COLOR] and [COLOR=Indigo]/dev/hda2[/COLOR], make sure they are ntfs, not ext3, and delete those two lines, NOTHING ELSE. Save changes to fstab and close.

---

