---
title: "mounting windows partitions help"
date: 2006-08-11
forum: Desktop Environments
---

### Post by linux_baby on 2006-08-11
i need help for mounting my windows partitions under ubuntu....

thr is no fstab in /etc/....
if i search fstab using apt-cache search fstab, it finds pmount and its already installed......

just tell me in simple how i mount my windows partitions...my fdisk commands r in belows....

# fdisk -l

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1275    10241406    7  HPFS/NTFS
/dev/hda2            1276        7295    48355650    f  W95 Ext'd (LBA)
/dev/hda5            1276        3187    15358108+   7  HPFS/NTFS
/dev/hda6            3188        5099    15358108+   7  HPFS/NTFS
/dev/hda7            5100        6398    10434186    7  HPFS/NTFS
/dev/hda8   *        6399        7035     5116671   83  Linux
/dev/hda9            7036        7100      522081   82  Linux swap / Solaris
/dev/hda10           7101        7295     1566306   83  Linux
/dev/hda11           7101        7101           0+  83  Linux

Partition table entries are not in disk order

---

### Post by navymom on 2006-08-11
Try seeing if what you need is here.  It's all copy and paste so it should be easy.  I'd also bookmark this page.  It's become my Ubuntu bible.

[http://ubuntuguide.org/wiki/Ubuntu_dapper#Windows](http://ubuntuguide.org/wiki/Ubuntu_dapper#Windows)

---

### Post by givré on 2006-08-11
Be sure that you have an /etc/fstab file, this is quite important. Don't reboot if you don't have this file.
```
ls /etc | grep fstab
```
If it return nothing, you will have to recreate it.

---

### Post by tomtom_in_eire on 2006-08-11
Hi,

What is the version of Ubuntu you are using?
If there is no fstab, there is probably a problem with your distro... To my knowledge, fstab is needed to mount the partition, without any fstab file you wouldn't even be able to start the system!

---

### Post by Concrete on 2006-08-11
> **navymom said:**
> Try seeing if what you need is here.  It's all copy and paste so it should be easy.  I'd also bookmark this page.  It's become my Ubuntu bible.

[http://ubuntuguide.org/wiki/Ubuntu_dapper#Windows](http://ubuntuguide.org/wiki/Ubuntu_dapper#Windows)


Woow, tnx mate for this excelent wikipedia site. Great stuf for amater user`s of ubuntu!

---

### Post by chedabob on 2006-08-11
mounting windows files is pretty easy. i find that its easiest to conver the partition to fat32, because both o/s support it natively. 

then in linux, bring up terminal, and type sudo nano -w /etc/fstab

when it loads scroll to the bottom line, and in the first column, put /dev/hdX, when X is the drive. if its your primary master, its a, if its primary slaves, its b, if its secondary master, its c, and if its secondary slave its d. for me, i use /dev/hdb, because its my primary slave.

press Tab, and then type a directory to mount to. personally, i use /home/matt/windoze

in the next column, put vfat, then in the next, defaults. in the final two, put 0.

then press Ctrl + O to save, then Ctrl + X to quit. 

do a reboot, then go into the directory you chose, and your files should be there.

thats my way of doing it.

---

### Post by varean on 2006-08-11
I assume your windows partition is NTFS, so add this line to your /etc/fstab file:

```
/dev/hdaX   /mnt/location/of/Win         NTFS    defaults             0 0
```

Where /dev/hdaX is the location of the Windows parition you want to mount/  Add the line repeatedly to the fstab with different /dev/hdaX sections to add multiple windows partition mounts to the fstab.  After that, reboot it and then the partition(s) will be autloaded.

---

### Post by chedabob on 2006-08-11
thats pretty much what i said, but i wasnt aware NTFS was supported natively yet? i know read support is sound, but write support is flaky, so i steered away from that and used fat32 instead. Partition magic for windows can convert an NTFS partition to fat32 without any loss of data.

---

