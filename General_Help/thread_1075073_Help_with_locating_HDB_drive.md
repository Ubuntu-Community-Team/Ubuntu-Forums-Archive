---
title: "Help with locating HDB drive"
date: 2009-02-19
forum: General Help
---

### Post by Indyviews on 2009-02-19
I have switched back to a dual boot, Ubuntu 8.10 being the default. Although my slave drive is detected in BIOS, it isn't in Ubuntu. In times past it was listed as something like Vol 1 Disk 1. Both drives are Sata 160 gig and I use the extra drive for storage, does anyone have a suggestion of what I can do to access it?

---

### Post by taurus on 2009-02-19
What filesystem is that second harddrive?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by Indyviews on 2009-02-19
Hi Tarus, not quite sure of what you mean, the disk is full and was done so while using Windows 2000. I have reinstalled Ubuntu a number of times and Ubuntu has detected it.

I ran the above and got:

steve@steve-desktop:~$ sudo fdisk -l
[sudo] password for steve: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1249f2ac

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         765     6144831    7  HPFS/NTFS
/dev/sda2             766       19457   150143490    5  Extended
/dev/sda5             766       19187   147974683+  83  Linux
/dev/sda6           19188       19457     2168743+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table
steve@steve-desktop:~$ 


I installed 2000 first on a 6gig partition and then told Ubuntu to use the rest of the drive.

---

### Post by taurus on 2009-02-19
If you want to use that extra harddrive as a storage, you first need to mount it before you can access it.

---

### Post by Indyviews on 2009-02-19
Thanks for the information Taurus.

---

### Post by taurus on 2009-02-19
Looks like you need to create a partition on the second harddrive, /dev/sdb1, and format it (whatever filesystem you want to use) before you can use it.  Install gparted and use it to do all that if you want.

```
sudo apt-get update
sudo apt-get install gparted
gksudo gparted
```

---

### Post by Indyviews on 2009-02-19
I am a bit wary of Gparted...twice I have used it from the Ubuntu disk and two days ago although I didn't mess with the windows partition, it leaves a Grub 22 error. (all I did was delete an extra swap partition. I had to do complete reinstalls.

I realize perhaps doing this on the terminal perhaps isn't the same thing but I don't believe I want to try that just yet.

---

