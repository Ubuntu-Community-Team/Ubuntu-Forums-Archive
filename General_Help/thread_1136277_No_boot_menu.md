---
title: "No boot menu?"
date: 2009-04-24
forum: General Help
---

### Post by Roxlo on 2009-04-24
I just installed Ubuntu to have it dual booting with Windows, however after the restart no boot menu came up, and it automatically keeps going to Windows. What can I do to get it to go to Ubuntu?

---

### Post by meierfra. on 2009-04-24
If you have more than one hard drive, see what happens if you change the boot order in your bios.

**If this did not solve your problem:**

In order to get a clearer picture of your setup, I suggest to boot  from the Ubuntu LiveCD and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post,  highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by Roxlo on 2009-04-24
```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x08bc08bb

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   972,157,409   972,157,347   7 HPFS/NTFS
/dev/sda2         972,157,410   976,768,064     4,610,655   5 Extended
/dev/sda5         972,157,473   976,430,699     4,273,227  83 Linux
/dev/sda6         976,430,763   976,768,064       337,302  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="3AB88543B884FE9F" TYPE="ntfs" 
/dev/sda5: UUID="633dbe5f-a75e-4e74-a78e-49176f0f08e1" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="5ec02ee5-d902-46d5-b2c6-823377b926b0" TYPE="swap" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=633dbe5f-a75e-4e74-a78e-49176f0f08e1 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=5ec02ee5-d902-46d5-b2c6-823377b926b0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 499.1GB: boot/vmlinuz-2.6.28-11-generic
 499.1GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde sdf 
```

---

### Post by meierfra. on 2009-04-24
> ```
Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   972,157,409   972,157,347   7 HPFS/NTFS
/dev/sda2         972,157,410   976,768,064     4,610,655   5 Extended
/dev/sda5         972,157,473   976,430,699     [COLOR="Red"]4,273,227 [/COLOR] 83 Linux
/dev/sda6         976,430,763   976,768,064       337,302  82 Linux swap / Solaris
```

4,273,227  sectors are about 2GB. But the minimum requirement for Ubuntu 9.04 is 4GB.  So I suggest to reinstall. I  recommend to give Ubuntu at least 10 GB.

---

