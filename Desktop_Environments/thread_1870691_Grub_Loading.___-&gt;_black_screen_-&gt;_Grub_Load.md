---
title: "Grub Loading.   -&gt; black screen -&gt; Grub Loading.  and so on, does not boot menu"
date: 2011-10-27
forum: Desktop Environments
---

### Post by yoramdavid on 2011-10-27
I have dual booting system: Ubuntu 11.10 and Windows XP. Today, after booting into windows, and rebooting, BURG wont load anymore.
I get this "Grub Loading." then a black screen followed by "Grub Loading."
It goes like this until I switch the computer off.
I have BURG doing the boot, but the message is from Grub.
BURG is installed into it own partition of 200MB, on the firs sector of the hard drive.

I managed to boot with a USB pen in Ubuntu 10.10.
I read some threads with similar problems and ran the command sudo ```
burg-update
```
And got the following message:
```
sudo: burg-update command not found
```

I am going to use the "boot_info_script*.sh" and post it here.

Thanks.

---

### Post by yoramdavid on 2011-10-27
The result is quite long, I am posting only the first part:

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 4 for /burg.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /etc/fstab

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda6 starts 
                       at sector 68. But according to the info from fdisk, 
                       sda6 starts at sector 67665848.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/grub.cfg /burg/burg.cfg /burg/core.img

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.02 2010-07-21
    Boot sector info:   Syslinux looks at sector 1453944 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the #oot\syslinux 
                       directory. The integrity check of the ADV area failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *        417,693    46,877,669    46,459,977   7 NTFS / exFAT / HPFS
/dev/sda2          46,877,731   223,303,499   176,425,769   5 Extended
/dev/sda5          46,877,733    67,665,779    20,788,047  83 Linux
/dev/sda6          67,665,848   220,733,099   153,067,252   7 NTFS / exFAT / HPFS
/dev/sda7         220,733,163   223,303,499     2,570,337  82 Linux swap / Solaris
/dev/sda3         223,313,920   234,432,511    11,118,592   7 NTFS / exFAT / HPFS
/dev/sda4               2,048       415,743       413,696  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 8059 MB, 8059355136 bytes
211 heads, 63 sectors/track, 1184 cylinders, total 15740928 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *              1    15,740,927    15,740,927   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        B6C4C919C4C8DD2D                       ntfs       Windows XP
/dev/sda3        F0A6C30EA6C2D3EE                       ntfs       Trabalhando
/dev/sda4        9817e6cc-396e-480c-a86f-5e043f29a7ea   ext4       
/dev/sda5        2261122c-7b08-4e5b-ba83-161c4f949e27   ext4       
/dev/sda6        01C7F0DDE3954E00                       ntfs       Documentos
/dev/sda7        7ea31e8d-711d-4f06-8558-d5cf1e20a9ea   swap       
/dev/sdb1        F097-CB16                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/Windows XP        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda4        /media/9817e6cc-396e-480c-a86f-5e043f29a7ea ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda5        /media/2261122c-7b08-4e5b-ba83-161c4f949e27 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=3 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /TUTag=AVKIML noguiboot 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional (TuneUp Backup)" /noexecute=optin /fastdetect /TUTag=AVKIML-BAK 
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/stage2                               0

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sda5 :
UUID=2261122c-7b08-4e5b-ba83-161c4f949e27	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sda4 :
UUID=9817e6cc-396e-480c-a86f-5e043f29a7ea	/boot	ext4	defaults	0	2
#Entry for /dev/sda6 :
UUID=01C7F0DDE3954E00	/media/Documentos	ntfs-3g	defaults,nosuid,nodev,locale=pt_PT.UTF-8	0	0
#Entry for /dev/sda3 :
UUID=F0A6C30EA6C2D3EE	/media/Trabalhando	ntfs-3g	defaults,locale=pt_PT.UTF-8	0	0
#Entry for /dev/sda7 :
UUID=7ea31e8d-711d-4f06-8558-d5cf1e20a9ea	none	swap	sw	0	0


--------------------------------------------------------------------------------

---

### Post by MoonLitOwl on 2011-10-27
You may very well have to uninstall Ubuntu and then reinstall it. Give that a try and see if it will load properly.

---

### Post by yoramdavid on 2011-10-27
I am able to boot into windows with super grub disk.
When trying to boot into Ubuntu with super grub disk, I get a "Error 15: File not found. Booting 'no lucky'.
Super Grub disk cannot fix grub. Perhaps because it is not installed?

What else to do??

---

### Post by yoramdavid on 2011-10-27
> **MoonLitOwl said:**
> You may very well have to uninstall Ubuntu and then reinstall it. Give that a try and see if it will load properly.

That means loosing everything, I was hoping not to have to do that.

---

### Post by yoramdavid on 2011-10-27
I have booted into Ubuntu 10.10 from the USB pen.
The Upgrade manager is asking if I want to upgrade to 11.10.
Can the system actually installed on the hard drive be updated if I am running another system from the USB pen?

---

### Post by yoramdavid on 2011-10-27
> **MoonLitOwl said:**
> You may very well have to uninstall Ubuntu and then reinstall it. Give that a try and see if it will load properly.

I used "Boot-repair" and solved my problem. Thank you.
Following these instructions here:
[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

---

