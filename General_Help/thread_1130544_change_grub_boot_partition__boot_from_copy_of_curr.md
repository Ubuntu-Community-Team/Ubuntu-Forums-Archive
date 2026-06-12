---
title: "change grub boot partition / boot from copy of current drive"
date: 2009-04-19
forum: General Help
---

### Post by stim on 2009-04-19
I have the latest Intrepid installed at /dev/sda6.  I partitioned my drive and used gparted to make a copy of /dev/sda6 into/dev/sda1.

I then ran a check on /dev/sda1 and gparted ran resize2fs and f2sck with no errors. 

If possible, I would now like to boot from this copy of my current 'working' partition.  /dev/sda6 is much smaller than /dev/sda1 . I have read that I cannot resize /dev/sda6 since it is the "end" --> of the drive, (correct me if I am wrong).

```

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7870    63215743+  83  Linux
/dev/sda2            7871        9729    14932417+   5  Extended
/dev/sda5            9660        9729      562243+  82  Linux swap / Solaris
/dev/sda6            7871        9659    14370079+  83  Linux

Partition table entries are not in disk order

```


it seems as though /dev/sda1 is flagged as boot, although I think that just might mean where grub is installed, and I need to do something with grub.  So I tried the suggestions from this thread:[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

so from my live-usb disk I followed the directions about halfway down the page:
```


sudo mkdir /mnt/root
sudo mount -t ext3 /dev/sda6 /mnt/root
sudo mount -t proc none /mnt/root/proc
sudo mount -o bind /dev /mnt/root/dev
sudo chroot /mnt/root /bin/bash
sudo grub

grub> find /boot/grub/stage1
 (hd0,0)
 (hd0,5)

grub> root (hd0,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

grub> 


```

but when I boot, it still boots into /dev/sda6.  Can anyone help me?

---

### Post by joshedmonds on 2009-04-20
You need to do is edit /boot/grub/menu.lst on sda1. Grub is now set up to use the settings from this file, however none of these settings (including the root location for your default boot) have been changed.

---

### Post by stim on 2009-04-20
After all that I did, I guess I installed grub correctly I just forgot one step.

I changed my root filesystem in /etc/fstab from sda6 to sda1....

:)

---

