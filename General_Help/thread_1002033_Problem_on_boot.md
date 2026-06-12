---
title: "Problem on boot"
date: 2008-12-04
forum: General Help
---

### Post by iSTRONG on 2008-12-04
Hi,

I'm dual-booting XP and Ubuntu 8.10.

When i restart my PC from XP, and try to boot linux - the booting freezes right before the login page. I just get a black screen and a blinking cursor. Nothing works at this point. not even CTL-ALT-DEL. I have to press the reset button to reboot. The interesting thing is that it boots into linux fine after that!

This happens every time.

Any ideas? any logs u want me to post?

---

### Post by iSTRONG on 2008-12-05
bump?

---

### Post by iSTRONG on 2008-12-05
please? I can post any logs you want.

new potentially relevant info:
This problem seems to have started (I'm not 100% sure that it was) after i installed the Ext2 IFS drivers on windows. However i have uninstalled the drivers since and the problem has remained.

---

### Post by Grolsche on 2008-12-05
Sounds like a graphics card error. What Card you got installed?

---

### Post by caljohnsmith on 2008-12-05
> **iSTRONG said:**
> please? I can post any logs you want.

new potentially relevant info:
This problem seems to have started (I'm not 100% sure that it was) after i installed the Ext2 IFS drivers on windows. However i have uninstalled the drivers since and the problem has remained.
Are you using Intrepid? If so, the Ext2IFS program in Windows could be a problem, because Intrepid now formats its Ext3 partitions to use a file system inode size of 256 bytes vs. 128 bytes that previous Ubuntu releases used; unfortunately Ext2IFS currently cannot handle the newer 256 byte inode size Ext3 partitions. That might have caused your problem.

How about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and post the output of:
```
sudo fdisk -lu
```
From the above output, determine which is your Ubuntu partition in the form sdXY (like sda2 or similar) by noticing which partition is "linux" under the "system" category, and then use that as follows:
```
sudo fsck -y /dev/sdXY
```
And please post the output.

---

### Post by iSTRONG on 2008-12-05
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders, total 293046768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x12f53ec5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      996029      497983+  83  Linux
/dev/sda2          996030     4899824     1951897+  82  Linux swap / Solaris
/dev/sda3         4899825   168200549    81650362+  83  Linux
/dev/sda4   *   168200550   293041664    62420557+   7  HPFS/NTFS

Disk /dev/sdb: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders, total 293046768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000ab159

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   293041664   146520801    7  HPFS/NTFS

Disk /dev/sdc: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders, total 586114704 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0f800000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   586099394   293049666   83  Linux

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5f32f7f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63   976768064   488384001    7  HPFS/NTFS




so it's sda1 (/boot parition), sda2 (swap), sda3 (root partition) & sdc1 (home partition)


sdc1 is the one i tried to access with the ext2 drivers... but as you said, it didn't work because of the 256 bytes node thingy...


ubuntu@ubuntu:~$ sudo fsck -y /dev/sda1
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
/dev/sda1: clean, 38/249368 files, 57060/497983 blocks


ubuntu@ubuntu:~$ sudo fsck -y /dev/sda2
fsck 1.41.3 (12-Oct-2008)
fsck: fsck.swap: not found
fsck: Error 2 while executing fsck.swap for /dev/sda2


ubuntu@ubuntu:~$ sudo fsck -y /dev/sda3
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
/dev/sda3: clean, 136835/5103616 files, 1242415/20412590 blocks (check in 5 mounts)

ubuntu@ubuntu:~$ sudo fsck -y /dev/sdc1
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
/dev/sdc1: clean, 51373/18317312 files, 50563547/73262416 blocks

---

### Post by caljohnsmith on 2008-12-05
[QUOTE=iSTRONG]When i restart my PC from XP, and try to boot linux - the booting freezes right before the login page. I just get a black screen and a blinking cursor. Nothing works at this point. not even CTL-ALT-DEL. I have to press the reset button to reboot. The interesting thing is that it boots into linux fine after that!
[/QUOTE]
So if you do a cold start, does Ubuntu boot OK? If Ubuntu only has problems booting after you restart from Windows, you might try doing a Ctrl-Alt-Del at the Grub menu before booting into Ubuntu so that Grub reboots; then see if you can boot into Ubuntu OK.

---

### Post by iSTRONG on 2008-12-10
> **caljohnsmith said:**
> So if you do a cold start, does Ubuntu boot OK? If Ubuntu only has problems booting after you restart from Windows, you might try doing a Ctrl-Alt-Del at the Grub menu before booting into Ubuntu so that Grub reboots; then see if you can boot into Ubuntu OK.

Thanks Caljohnsmith.

Cold start works fine as long as my previous boot was in Ubuntu and not XP...

I tried doing Ctrl-alt-del at the Grub Menu after restarting from XP and Ubuntu booted fine...

What now? is there a permanent solution?

---

### Post by caljohnsmith on 2008-12-10
> **iSTRONG said:**
> Thanks Caljohnsmith.

Cold start works fine as long as my previous boot was in Ubuntu and not XP...

I tried doing Ctrl-alt-del at the Grub Menu after restarting from XP and Ubuntu booted fine...

What now? is there a permanent solution?
I don't know of a permanent solution off-hand, but maybe the problem is related to how you have your BIOS set up. You might want to poke around your BIOS and see what the settings are, because your strange reboot behavior could have something to do with your BIOS configuration.

---

### Post by iSTRONG on 2008-12-10
It's not the bios because i had the setup working fine for a while under the same bios settings. The problem only occured when (or shortly after) i installed the etx2 IFS drivers... (I've uninstalled them since but the problem has remained)

---

