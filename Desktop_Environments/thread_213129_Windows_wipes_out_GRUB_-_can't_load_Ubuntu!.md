---
title: "Windows wipes out GRUB - can't load Ubuntu!"
date: 2006-07-10
forum: Desktop Environments
---

### Post by vincebs on 2006-07-10
Hello everyone,

Could someone help me restore GRUB? Here's what I have done so far:

1.) Booted from Dapper Drake LiveCD
2.) I type sudo grub-install /dev/sda5 and get:
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.

3.) Mounted my Linux partitions under /mnt/linux. I have two linux partitions: one at /dev/sda7 which was mounted under /, and one at /dev/sda5 which was mounted under /boot/
So I typed in "sudo mount /dev/sda7 /mnt/linux/" and "sudo mount /dev/sda5 /mnt/linux/boot"

4.) Then I typed "sudo mount -o bind /proc /mnt/linux/proc"
5.) I sudo chroot /mnt/linux.
6.) sudo grub-install /dev/sda5 returns:
sudo: unable to lookup ubuntu via gethostbyname()

7.) I type sudo grub, get "sudo: unable to lookup ubuntu via gethostbyname()"
8.) I type grub. I enter grub.
9.) find /boot/grub/stage1 returns: Error 15: File Not Found
10.) I type root (hd0,4) (since /boot was at /dev/sda5), I get Error 21: Selected disk does not exist
11.) I type root (sd0,4), I get Error 23: Error while parsing number
12.) I type grub-install /dev/sda5 (without sudo), get:
/dev/sda5: Not found or not a block device.

What should I do?

Some helpful information:
Before chroot, if I type sudo fdisk -l, I get:


Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           8       64228+  de  Dell Utility
/dev/sda2   *           9        6087    48829567+   7  HPFS/NTFS
/dev/sda3            6088        7295     9703260    5  Extended
/dev/sda5   *        6088        6098       88326   83  Linux
/dev/sda6            6099        6160      497983+  82  Linux swap / Solaris
/dev/sda7            6161        6641     3863601   83  Linux
/dev/sda8            6642        7295     5253223+   b  W95 FAT32


After chrooting, if I type fdisk -l, I get nothing.

My menu.lst had the following entry for Ubuntu:

title           Linux 2.6.15-23-386
root            (hd0,4)
kernel          /vmlinuz-2.6.15-23-386 root=/dev/sda6 ro quiet splash
initrd          /initrd.img-2.6.15-23-386
savedefault
boot


Help!

---

### Post by subzero79 on 2006-07-10
Maybe you should try

```
sudo grub-install /dev/sda
```

remember you are installing grub to the MBR, first 512 bytes of the hard drive, not a partition.

---

### Post by vincebs on 2006-07-10
> **subzero79 said:**
> Maybe you should try

```
sudo grub-install /dev/sda
```

remember you are installing grub to the MBR, first 512 bytes of the hard drive, not a partition.

Whoops, forget to mention I tried that step. Thanks anyway!

$ sudo grub-install /dev/sda
Could not find device for /boot: Not found or not a block device.

---

### Post by vincebs on 2006-07-11
It still doesn't work

Anyone have more ideas?

Thanks,
Vince

---

### Post by subzero79 on 2006-07-11
Have a try on this guide

[http://ubuntuforums.org/showthread.php?t=24113&highlight=restore+grub](http://ubuntuforums.org/showthread.php?t=24113&highlight=restore+grub)

on the first reply.

---

### Post by vincebs on 2006-07-11
> **subzero79 said:**
> Have a try on this guide

[http://ubuntuforums.org/showthread.php?t=24113&highlight=restore+grub](http://ubuntuforums.org/showthread.php?t=24113&highlight=restore+grub)

on the first reply.

Did you read my post?

More precisely, the following line I wrote:
[QUOTE=vincebs]
10.) I type root (hd0,4) (since /boot was at /dev/sda5), I get Error 21: Selected disk does not exist[/QUOTE]

I've gone through that whole thread, I've tried everything that seems to apply to my situation.

Any more ideas?

---

### Post by subzero79 on 2006-07-12
Have a try otherwise on grub super disk, here.

[http://adrian15.raulete.net/grub/tiki-index.php](http://adrian15.raulete.net/grub/tiki-index.php)

You should be able to do it from a boot CD, floopy or pendrive.

---

### Post by vincebs on 2006-07-17
I also tried typing update-grub after chrooting

It didn't work either.

Any more ideas?

---

### Post by stinkball on 2006-07-17
I have the same problem. i don't know how grub got wiped on your pc, but on mine my MBR just randomly screwed up when i turned on my computer this morning. so i restored the MBR with my windows install cd and I can't get grub to install again.  I've tried everything you've listed also.  It's a shame because everything was running very smoothly in ubuntu... And I don't want to reinstall everythign. grrr :confused:

---

