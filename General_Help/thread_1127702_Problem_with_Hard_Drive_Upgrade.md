---
title: "Problem with Hard Drive Upgrade"
date: 2009-04-16
forum: General Help
---

### Post by emid on 2009-04-16
For reasons that I won't get into (they really don't matter for the issue at hand) I have been running my desktop linux install on a 40 GB IDE 5400 RPM drive.  Today I remembered that I had a 160 GB SATA 7200 RPM drive sitting in the closet.  Not wanting to reinstall and have to reconfigure everything, I booted up a Knoppix cd and used gparted to copy all the partitions from the 40GB drive to the 160GB drive.  Everything looked good, I mounted the drive while booted into Knoppix and it seemed that everything had copied over.

Now, I assumed that this wasn't going to *JUST* work. :D  I booted up the system with the new drive just to try it.  I'm getting an error that says "Missing operating System".

Before I start messing around trying to figure out what I'm missing, I wanted to ask you guys what you think the issue is?  Is it grub related, or maybe something else?

I should also note that I have 3 additional SATA drives in this box. I have them set up in a RAID 5 using mdadm.

Anyways, any input would be appreciated before I go ahead and start doing some real damage. :D

---

### Post by codeseer on 2009-04-16
I'd say it's grub. Maybe reinstalling grub to the drive would work?

This is assuming you have everything correct in the BIOS.

---

### Post by 123456789123456789123456 on 2009-04-16
codeseer is correct, the issue is Grub, you no longer have a boot loader.  Let me explain, with normal copying processes, the following are coppied, your main partition, sda0,1 and the swap partition, possible sda0,2.  in sda0,1 is gurb stage 1.5.  which actually boots the OS, but the program you used did not copy the contents of MBR to the new drive, so without grub stage 1, located in the Master Boot Record, the OS is unable to boot, error whould be either no OS, or even possibly no boot device, depending on how the BIOS is set up.  Solution, with either super grub disk, or you may be able to use the ubuntu live cd, reinstall Grub, into the MBR, and in turn that will replace stage 1.5 in the main partition of the sata drive.  The OS should boot afterword.

the best way to do what you wanted would have been to use a disk cloner.  One that makes a direct clone of the original drive, including MBR, and all subsiquent partitons, some even clone the serial number.  The result is two identical disks, at least as far as the computer BIOS is concerned.

---

### Post by codeseer on 2009-04-16
[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by emid on 2009-04-16
> **codeseer said:**
> [http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

I tried reinstalling grub as explained in that thread but it didn't work.  I still get the same "Missing Operating System".

The 160GB drive is definitely set up correctly in the BIOS. (Just thought I'd throw that in there)

---

### Post by emid on 2009-04-16
Here's my result for "fdisk -l" when I'm booted into the Ubuntu live CD:
```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00095c55

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a93aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007348a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x034b74c9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       18834   151284073+  83  Linux
/dev/sdd2           18835       19457     5004247+   5  Extended
/dev/sdd5           18835       19457     5004216   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 


```

I have the three 500GB SATA drive which are normally set up in the RAID 5, and I have the new 160GB SATA drive which I copied my linux partitions onto.

I noticed that /dev/sda1 has a boot flag on it.  Could that be related to my problem?  I didn't change anything with regards to any of the 500 GB drives today, so I'm hesitant to assume that is the issue.

---

### Post by codeseer on 2009-04-16
I'd check the /boot/grub/device.map and /boot/grub/menu.lst files for sdd1 and make sure all of that got detected properly.

---

### Post by emid on 2009-04-16
I just checked both of those and they look fine.  I was scratching my head because it doesn't make sense, so I redid the grub tutorial and now I'm up and running with no problems.  I guess I mistyped something, which only added to my confusion.

Anyways, much thanks for the help, I appreciate it.

---

