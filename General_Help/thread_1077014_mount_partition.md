---
title: "mount partition"
date: 2009-02-21
forum: General Help
---

### Post by kaykav on 2009-02-21
Good evening,
                  Ok I tried almost evrything; I have a bootloader menulist,
consisting of ubuntu 8.04 and windows xp. I can boot into windows, but the error message I get is ubuntu partition is not mounted. How do I mount it so I can boot into it? I have a live cd but I'm mot sure as to the correct commands to write. How does a Primary OS partition get un-mounted? I installed grub from the live cd 'successfully' to no avail.

                                            Thank you ....Rich

---

### Post by taurus on 2009-02-21
Did you install Ubuntu on it own partition or from windows--wubi?

From the Ubuntu LiveCD, open a terminal and post the output of this command.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by kaykav on 2009-02-22
ok...../dev/sda2 is ubuntu.
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f800000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sda2            6375        9486    24997140   83  Linux
/dev/sda3            9487       38913   236372314+   f  W95 Ext'd (LBA)

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f8000b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2611    20972826    7  HPFS/NTFS
/dev/sdb2            2612        5222    20972857+   7  HPFS/NTFS
/dev/sdb3            5223       38913   270622957+   f  W95 Ext'd (LBA)
/dev/sdb4           38914       38914           0   a5  FreeBSD

Disk /dev/sdg: 257 MB, 257949696 bytes
64 heads, 32 sectors/track, 246 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Disk identifier: 0x90909090

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1         246      251888    e  W95 FAT16 (LBA)

---

### Post by taurus on 2009-02-22
Mount /dev/sda2 and have a look at /etc/fstab & /boot/grub/menu.lst to make sure everything is good for /dev/sda2.

```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sda2 /media/ubuntu
cat /media/ubuntu/boot/grub/menu.lst
cat /etc/fstab
sudo blkid
```
Interesting that you only have root partition, /, but no swap partition.  Also, /dev/sda3 (extended partition) is not being used at all.

---

### Post by kaykav on 2009-02-22
Hey Taurus,
                 Thanks for your input. I simply reinstalled the ubuntu distro. It gave me the option to save my existing documents. All is well.
     My sda drive was knotted up with Logical volumes and another linux distro(mandriva 2009) .I still have to take control of installing grub to the correct place when I install an additional distro, in the future. It's all a learning process. Once again   Thank you...Rich

---

