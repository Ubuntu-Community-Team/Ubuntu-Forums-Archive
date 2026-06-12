---
title: "Can't boot windows, grub error 22"
date: 2009-02-16
forum: General Help
---

### Post by geddylee on 2009-02-16
So i deleted my linuxmint partitions and resized my windows partition because i never used it and needed the space for visual studio and now i can't boot anymore.

I'm having the grub problem with the error 22. I downloaded the ms-sys package installed it and followed the directions, but it still didn't work, my computer still hangs at the grub loading error 22. also when i try to do sudo ms-sys -m/dev/hda(or sda) it says "unable to open -m/dev/sda(hda), no such file or directory".

im at a loss of what to do here. to make it worse, at some point while i was trying the mssys, all partitions dissapeared from my fdisk -l except for sda1 which appears to be the useless recovery partition that comes with my computer. it is set as the boot. the partition containing my windows is hda1. i don't think it's gone because it still shows up in gnome partitioner. however i made a bootable dos disk with nero and when i do fdisk it shows what would be my main partition as free space. :(

so if anyone has any suggestions of what i should do i would really appreciate it.

---

### Post by Altay_H on 2009-02-16
Did you try [Super Grub]("http://www.supergrubdisk.org/index.php?pid=5")?

It should help you restore or remove your GRUB.

---

### Post by geddylee on 2009-02-16
i downloaded boot_info_script025.sh and ran it and here's what i got hope this helps:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/hda and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/hdb
 => No boot loader is installed in the MBR of /dev/hdc
 => Windows is installed in the MBR of /dev/sdf

hda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /BOOT.INI /ntldr /NTLDR /NTDETECT.COM 
                       /ntdetect.com

hda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTLDR /NTDETECT.COM /ntdetect.com

hda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

hda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

hdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdf1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive hda: _____________________________________________________________________

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot         Start           End          Size  Id System

/dev/hda1          11,068,785   232,412,354   221,343,570   7 HPFS/NTFS
/dev/hda2    *             63    11,068,784    11,068,722   b W95 FAT32
/dev/hda4         232,862,175   234,436,544     1,574,370   5 Extended
/dev/hda5         232,862,238   234,436,544     1,574,307  82 Linux swap / Solaris


Drive hdb: _____________________________________________________________________

Disk /dev/hdb: 15.3 GB, 15367790592 bytes
255 heads, 63 sectors/track, 1868 cylinders, total 30015216 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot         Start           End          Size  Id System

/dev/hdb1                  63    30,009,419    30,009,357   7 HPFS/NTFS


Drive hdc: _____________________________________________________________________
Note: sector size is 2048 (not 512)

Disk /dev/hdc: 732 MB, 732643328 bytes
255 heads, 63 sectors/track, 22 cylinders, total 357736 sectors
Units = sectors of 1 * 2048 = 2048 bytes

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found


Drive sdf: _____________________________________________________________________

Disk /dev/sdf: 4009 MB, 4009754624 bytes
216 heads, 32 sectors/track, 1133 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot         Start           End          Size  Id System

/dev/sdf1    *             32     7,831,551     7,831,520   c W95 FAT32 (LBA)

/dev/sdf1 ends after the last cylinder of /dev/sdf

blkid -c /dev/null: ____________________________________________________________

/dev/hda1: TYPE="ntfs" 
/dev/hda2: UUID="423B-2BDF" TYPE="vfat" 
/dev/hda5: UUID="a40e0072-e651-4938-8d04-70a2b5c35f19" TYPE="swap" 
/dev/hdb1: TYPE="ntfs" 
/dev/evms/hda1: TYPE="ntfs" 
/dev/evms/hda2: UUID="423B-2BDF" TYPE="vfat" 
/dev/evms/hda5: UUID="a40e0072-e651-4938-8d04-70a2b5c35f19" TYPE="swap" 
/dev/evms/hdb1: TYPE="ntfs" 
/dev/sdf1: UUID="2060-2EF0" TYPE="vfat" 

=============================== "mount" output: ===============================

unionfs on / type unionfs (rw)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-26-386/volatile type tmpfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
/dev/sdf1 on /media/Lexar type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=999,gid=999,umask=077,iocharset=utf8)


================================ hda1/boot.ini: ================================

[boot loader]
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect

================================ hda1/BOOT.INI: ================================

[boot loader]
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 

```

---

### Post by caljohnsmith on 2009-02-16
How about from your Live CD do:
```
sudo apt-get install lilo
sudo lilo -M /dev/hda mbr
```
That will install a Windows equivalent MBR to your hda drive, so that should work to boot Windows again. But it also looks like you need to set the boot flag on the hda1 partition, because that appears to be your Windows partition:
```
sudo sfdisk -A1 /dev/hda
```
Then reboot, and let me know how far you get. We can work from there if necessary.

---

### Post by geddylee on 2009-02-16
i tried the super grub and thank you it seems to have worked to get my windows to boot again. chkdsk is running at the moment so i will let you guys know how it works out. Thanks again soo much for your quick responses and help. You guys are a lifesaver! 

Now i just have to install 10g worth of program and patch files to get my visual studio and wow back 
;)

---

