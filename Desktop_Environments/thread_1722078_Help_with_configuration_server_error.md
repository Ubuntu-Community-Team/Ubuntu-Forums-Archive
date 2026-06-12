---
title: "Help with configuration server error"
date: 2011-04-05
forum: Desktop Environments
---

### Post by shahid_kaleem on 2011-04-05
Hi

I recently installed ubuntu and at the time of installation i created 

1. ext4 as /
2. ext4 as /tmp
3. swap partition

After installation i installed windows and deleted /tmp partition and it became unallocated space.
Now at bootup it says cant mount /tmp press S to cancel or M for manual recovery.

I press S and it shows an error message (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)
So i used Live CD and converted that partition as ext4. I am thinking to mount that partition as /tmp would solve the problem. But not sure.

I need advice or it could be done without it.

Here is my what my hard disk look like at the moment

 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        5100       43345   307200000    7  HPFS/NTFS
/dev/sda2           43345       77096   271099609+  83  Linux
/dev/sda3           77097       77825     5855662    5  Extended
/dev/sda4               1        5099    40957686   83  Linux
/dev/sda5           77097       77825     5855661   82  Linux swap / Solaris

This used to be /tmp partition before.
/dev/sda4               1        5099    40957686   83  Linux 


Any help would be appreciated. I do not want to reinstall OS again not because i will lose anything but because this what i always do in linux and this time i want to correct the problem. So any solution other than reinstalling OS is much appreciated.

---

### Post by Krytarik on 2011-04-05
I suspect an old no more appropriate entry for those partition in "/etc/fstab".

So please post it, in code-tags please, the #-button in the editor.

Also see this guide:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Greetings.

---

