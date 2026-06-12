---
title: "Hibernation doesn't work [Ubuntu 8.10]"
date: 2009-02-14
forum: General Help
---

### Post by kulambi on 2009-02-14
I have been trying to hibernate my system (running Ubuntu 8.10) but it doesn't work. After booting from hibernation no applications are restored. All that i have tried to fix i have listed below. Please help.  

1) Swap parition was not allocated during installation, but later on I allocated a 4 GB (equal to RAM) space as swap parition (Linux / Solaris) using Live CD.

2) Output of fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           9       72261   de  Dell Utility
/dev/sda2              10        1315    10485760    7  HPFS/NTFS
/dev/sda3   *        1315       23540   178523128    7  HPFS/NTFS
/dev/sda4           23540       38914   123486208+   f  W95 Ext'd (LBA)
/dev/sda5           23540       26165    21087232   83  Linux
/dev/sda6           26166       29353    25600000    7  HPFS/NTFS
/dev/sda7           29353       32030    21503996    7  HPFS/NTFS
/dev/sda8           32030       32540     4094976   82  Linux swap / Solaris
/dev/sda9           32540       37639    40956924    7  HPFS/NTFS
/dev/sda10          37639       38914    10238976    7  HPFS/NTFS

3) Output of free -m, looks like swapping is being done

             total       used       free     shared    buffers     cached
Mem:          2998       1707       1291          0        737        430
-/+ buffers/cache:        538       2460
Swap:         3998          4       3994

4) I tried the following commands as well, set the RESUME=/dev/sda8 in "/etc/initramfs-tools/conf.d/resume" file

 sudo gedit /etc/initramfs-tools/conf.d/resume
 sudo dpkg-reconfigure initramfs-tools 
 sudo update-initramfs -u

5) I have added an entry in /etc/fstab

/dev/sda8	none 	swap 	sw 	0 	0

6) This is the output from /var/log/pm-suspend.log 

Initial commandline parameters: 
Fri Feb 13 21:11:57 IST 2009: Running hooks for hibernate.
/usr/lib/pm-utils/sleep.d/00clear hibernate: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate: success.
/usr/lib/pm-utils/sleep.d/05led hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/10NetworkManager hibernate: success.
/usr/lib/pm-utils/sleep.d/48hid2hci hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/49bluetooth hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/50modules hibernate: success.
/usr/lib/pm-utils/sleep.d/90clock hibernate: Welcome to PulseAudio! Use "help" for usage information.
>>> success.
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate: success.
/usr/lib/pm-utils/sleep.d/95anacron hibernate: success.
/usr/lib/pm-utils/sleep.d/95led hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/96laptop-mode hibernate: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video hibernate: success.
/usr/lib/pm-utils/sleep.d/99video hibernate: success.
Fri Feb 13 21:12:01 IST 2009: performing hibernate

Thanks in advance :-)

---

