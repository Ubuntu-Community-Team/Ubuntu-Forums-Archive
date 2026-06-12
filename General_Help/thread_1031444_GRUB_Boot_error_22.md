---
title: "GRUB Boot error 22"
date: 2009-01-05
forum: General Help
---

### Post by notrace on 2009-01-05
I was messing around with partitions hoping to reinstall ubuntu, i restart from gparted live cd and then bam! this error message. 

I have tried booting from my windows CD, and with the ubuntu CD yet the error message comes up again. I've changed the boot order but it still comes up. I've tried everything and i can't do anything with it atm!

Please help!

thanks in advance.

notrace

---

### Post by caljohnsmith on 2009-01-05
In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. If you don't have internet connectivity when using the Live CD, you can instead right-click [this link]("http://home.comcast.net/~ubuntu_grub/boot_info_script.txt") to the script in your web browser, choose "Save link as...", save the "boot_info_script.txt" file, transfer it to your Ubuntu desktop on the Live CD via USB stick, floppy, or however you want to do it, and then do the following in a terminal:
```
sudo bash ~/Desktop/boot_info_script.txt
```
The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by notrace on 2009-01-05
> **caljohnsmith said:**
> In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. If you don't have internet connectivity when using the Live CD, you can instead right-click [this link]("http://home.comcast.net/~ubuntu_grub/boot_info_script.txt") to the script in your web browser, choose "Save link as...", save the "boot_info_script.txt" file, transfer it to your Ubuntu desktop on the Live CD via USB stick, floppy, or however you want to do it, and then do the following in a terminal:
```
sudo bash ~/Desktop/boot_info_script.txt
```
The results of that script will help clarify your setup and hopefully what your problem might be.

I would love to do that but i can't, i boot from the live cd and i get the error straight away! i literally can't do anything with the computer! I just get this boot error, quite frightening i might have reallty screwed it up.

---

### Post by caljohnsmith on 2009-01-05
The Live CD does not use Grub as its boot loader, so since you are getting a Grub error, most likely that is because you are actually booting your HDD and not the CD drive at this point. I would go into your BIOS and check that the CD drive is first in the BIOS boot order, but if it is, I would try booting another bootable CD in it, maybe a Windows Install CD for example. Let me know how that goes.

---

### Post by notrace on 2009-01-05
> **caljohnsmith said:**
> The Live CD does not use Grub as its boot loader, so since you are getting a Grub error, most likely that is because you are actually booting your HDD and not the CD drive at this point. I would go into your BIOS and check that the CD drive is first in the BIOS boot order, but if it is, I would try booting another bootable CD in it, maybe a Windows Install CD for example. Let me know how that goes.

Ah i have done it! I have managed to boot into ubuntu, i shall do what oyu said first cal :)

```
============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Win_98
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x913e1847

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   781412526   390706232    b  W95 FAT32

sfdisk -V /dev/sda:

Warning: partition 1 does not end at a cylinder boundary

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 8065 MB, 8065646080 bytes
8 heads, 32 sectors/track, 61535 cylinders, total 15753215 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1a221a21

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32    15753214     7876591+   b  W95 FAT32

sfdisk -V /dev/sdb:

Warning: partition 1 extends past end of disk

blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="FREECOM HDD" UUID="17E8-082F" TYPE="vfat" 
/dev/sdb1: LABEL="CRUZER" UUID="6E0A-0040" TYPE="vfat" 

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
/dev/sdb1 on /media/CRUZER type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)
/dev/sda1 on /media/FREECOM HDD type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)

=============================== StdErr Messages: ===============================

No errors were reported.
```

---

### Post by caljohnsmith on 2009-01-05
OK, that's great, I see you got your Live CD to boot. How about doing the following:
```
sudo apt-get install lilo
sudo lilo -M  /dev/sda mbr
sudo sfdisk -A1 /dev/sda

```
The first command installs the lilo package, the second command installs a Windows equivalent MBR (Master Boot Record) to your Windows sda drive, and the last command sets the sda1 Windows partition as active, i.e. bootable. If none of the above commands return an error, reboot, and let me know what happens when you boot the Windows drive. We can go from there. :)

---

