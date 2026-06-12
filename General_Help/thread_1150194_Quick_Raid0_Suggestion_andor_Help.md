---
title: "Quick Raid0 Suggestion and/or Help"
date: 2009-05-05
forum: General Help
---

### Post by aqualad on 2009-05-05
I'm running Windows on my 1TB raid0, I left some space for Ubuntu when I first installed windows, but now I can't find the best way to install Ubuntu without losing my data.

I just want to know the best way to set up a fakeraid or software raid with dual-boot.

Here's the situational information:

I have an Intel ICH9R on a Gigabyte GA-X48T-DQ6.  I'll use any version that will work, but so far 8.10 and 9.04 haven't worked for me.  I tried using dmraid in both 8.10 and 9.04 live, but upon issuing the command dmraid -ay I receive this output:
```
ubuntu@ubuntu:~$ sudo swapoff -a
ubuntu@ubuntu:~$ sudo dmraid -ay
ERROR: isw device for volume "Terorbyte" broken on /dev/sda in RAID set "isw_ebiaejciia_Terorbyte"
ERROR: isw: wrong # of devices in RAID set "isw_ebiaejciia_Terorbyte" [1/2] on /dev/sda
```

It seems to not recognize sda, here's the sudo fdisk -l output:
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc0000040

Disk /dev/sda doesn't contain a valid partition table
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: invalid flag 0x031a of partition table 5 will be corrected by w(rite)

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc396c396

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       25496   204796588+   7  HPFS/NTFS
/dev/sdb2           25497      121600   771955380    f  W95 Ext'd (LBA)
/dev/sdb5   ?      159371      228114   552172887+  1d  Unknown
```

I tried the autodetection through 8.10 alternate, but the installer just jumped to the red screen and told me that it had failed.

I would try mdadm, but it looks like it won't work with Windows on a dual-boot.

Help is appreciated, I hope you can come to my rescue one more time ubuntuforums!

---

### Post by fjgaude on 2009-05-06
You say you left space on the array... you mean that the raid0 array is on, say one partition and you have another partition that is not used by the array?

I've never done what you are trying to do.

Going with the LiveCD, installing dmraid on it if not there, then using the command:

**dmraid -ay** should show partitions that are used by Windows on raid0, not the free partitions that could be used to install Ubuntu.

If you don't see places that are free with just the live CD then you are screwed, I think. <smile>

---

