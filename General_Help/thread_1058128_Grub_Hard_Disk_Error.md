---
title: "Grub: Hard Disk Error"
date: 2009-02-02
forum: General Help
---

### Post by tchambers14 on 2009-02-02
Hi, I am having some problems after installing linux to an external hard drive. 

My original system did not have any linux formated drives on it, following the install the external HDD was capable of booting linux on my pc, however when trying to boot the computer from its original hard drive all I get is GRUB hard disk error. 
When booting ubuntu from a live cd I am unable to mount the original hard drives NTFS partitions. 

The output of sudo fdisk -l gives the following: -

isk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x37415088

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2611    20972826    7  HPFS/NTFS
/dev/sda2            2612       10011    59440500    f  W95 Ext'd (LBA)
/dev/sda5            2612       10011    59440468+   7  HPFS/NTFS

I would really appreciate any advice as I need to boot into my windows drives to recover some documents. 

Thanks

Tom

---

### Post by taurus on 2009-02-02
Do you have a windows CD?  You could use Super GRUB to recover your boot table for windows, [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html).

And if you want to mount your ntfs partitions from the LiveCD, try something like

```
sudo mkdir /media/sda1 /media/sda5
sudo mount -t ntfs-3g /dev/sda1 /media/sda1
sudo mount -t ntfs-3g /dev/sda5 /media/sda5
df -h
```

---

### Post by tchambers14 on 2009-02-02
After following your instructions I get the following error message in the terminal: - 

thomas@thomas-hdd:/media$ sudo mount -t ntfs-3g /dev/sda1 /media/sda1
Unexpected clusters per mft record (-127).
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

Have a messed up by windows boot partition?

---

### Post by caljohnsmith on 2009-02-02
It sounds like you may have accidentally installed Grub to the boot sector of your NTFS partition. In order to find out if that is the case and also get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

---

### Post by tchambers14 on 2009-02-02
Ran the boot info script the output of the Results.txt file are as follows: -
```

============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Boot sector info:  Grub is installed in the boot sector of sda1 and looks 
                       at sector 28917839 on boot drive #2 for the stage2 
                       file, but no stage2 files can be found at this 
                       location.
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Grub
    Boot sector info:  Grub is installed in the boot sector of sda2 and looks 
                       at sector 28983359 on boot drive #2 for the stage2 
                       file, but no stage2 files can be found at this 
                       location.

sda5: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Boot sector info:  Grub is installed in the boot sector of sda5 and looks 
                       at sector 28983367 on boot drive #2 for the stage2 
                       file, but no stage2 files can be found at this 
                       location.
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x37415088

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    41,945,714    41,945,652   7 HPFS/NTFS
/dev/sda2          41,945,715   160,826,714   118,881,000   f W95 Ext d (LBA)
/dev/sda5          41,945,778   160,826,714   118,880,937   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

=======Devices which don't seem to have a corresponding hard drive==============

 sdb .
 sdc .
 sdd .
 sde .

=============================== StdErr Messages: ===============================

/home/ubuntu/Desktop/boot_info_script024.sh: line 1043: [: =: unary operator expected
/home/ubuntu/Desktop/boot_info_script024.sh: line 1043: [: =: unary operator expected
```

I hope this helps. 

Thanks

Tom

---

### Post by caljohnsmith on 2009-02-02
Unfortunately you installed Grub to the boot sector of both your NTFS partitions, sda1 and sda5. As you have all ready found out the hard way, that makes those partitions unmountable and inaccessible. Just a word of caution, but when you run commands in the Grub command line, you should avoid doing "setup (hdX,Y)" unless you know for sure that you want to install Grub to the boot sector of partition (hdX,Y); (hdX,Y) should be a linux partition, not an NTFS, FAT, or other file system type. But to fix your problem, if you have a Windows XP Install CD, how about booting that, go to the "recovery console" and do:
```
map
```
That should give the drive letters of both your NTFS partitions, and then do:
```
fixboot C:
```
And replace "C" with the drive letter of each of your NTFS partitions. If that command completes successfully, you should be able to mount and access your NTFS partitions after that. Let me know how it goes or if you run into problems.

---

### Post by tchambers14 on 2009-02-03
Thank you so much, you are a life saver. I will be more careful in future!!

---

### Post by caljohnsmith on 2009-02-03
Glad to hear that worked OK and your NTFS partitions are accessible again. :)

---

