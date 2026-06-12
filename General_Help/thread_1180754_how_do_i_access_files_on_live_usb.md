---
title: "how do i access files on live usb?"
date: 2009-06-07
forum: General Help
---

### Post by ndcook on 2009-06-07
I have been looking for a solution for this for sometime. I have 2 partitions on a usb key. One is a windows fat32 and the second is a hidden ubuntu cd image. I'm running ubuntu live in persistent mode.

I followed the instructions from this website. 
[http://rudd-o.com/en/linux-and-free-...live-usb-drive]("http://rudd-o.com/en/linux-and-free-software/a-better-way-to-create-a-customized-ubuntu-live-usb-drive")

When I run the live usb and boot into Ubuntu i cannot access any of my files stored on the first partition. It tells me I have no mounting point. I only see the cd image. Under ubuntu. I can't store files to my usb within Ubuntu only under my casper-rw file. Do I need to edit my fstab?

my fdisk -l output is this. I need access to sdb1. gparted tells me it cannot find a mounting point?

Thanks


Disk /dev/sdb: 8032 MB, 8032092160 bytes
255 heads, 63 sectors/track, 976 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         886     7116763+   c  W95 FAT32 (LBA)
/dev/sdb2             887         976      722925   1c  Hidden W95 FAT32 (LBA)
ubuntu@ubuntu:~$

/etc/fstab
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0

---

### Post by blueridgedog on 2009-06-07
Well, have you tried mounting it by hand?

If your setup is persistent, you should be able to make a directory and mount it.

```

sudo mkdir /windowsfiles
sudo mount /dev/sdb1 /windowsfiles
```

You can mount it to any empty directory...what is in mnt and media?

sudo ls /media
sudo ls /mnt

---

### Post by ndcook on 2009-06-08
LOL...thanks for the reply. I got frustrated and tried just installing ubuntu directly to usb except my installation is messed up.

So I will redo the setup for the persistent live usb and give it a try.

---

