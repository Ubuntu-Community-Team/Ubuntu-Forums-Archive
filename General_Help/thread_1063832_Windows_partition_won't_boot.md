---
title: "Windows partition won't boot"
date: 2009-02-08
forum: General Help
---

### Post by GabrielWolff on 2009-02-08
I am using Ubuntu for years. Yet I need two WIN notation programs I can't install on Ubuntu (Finale & Sibelius).

I bought a new HDD, 
1) backing up the WIN partition on an external HDD, then 
2) installing Ubuntu on the new HDD, leaving space for the WIN partitions, and
3) copying the WIN partitions on the new HDD, using a gparted live CD.

However, they don't boot. In other words: I turn on the machine, and Ubuntu will boot automatically, giving me no other choice. I can see the partitions in Nautilus.

What do I have to do in order to make them bootable?

Attached is a screenshot of gparted as it looks right now.

---

### Post by caljohnsmith on 2009-02-08
Is your Windows XP or Vista? You might have a bit of trouble booting Windows from another HDD where you simply copied/pasted the partition to the new drive, especially if your new Windows partition does not begin at the same sector as the original Windows partition. Also, is the new drive Windows is on now SATA or IDE? In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and give a better idea of what it might take to boot Windows.

---

### Post by GabrielWolff on 2009-02-08
Here we go:
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /NTLDR /NTDETECT.COM

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0006cd07

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   257,361,299   257,361,237  83 Linux
/dev/sda2         306,536,265   312,576,704     6,040,440   5 Extended
/dev/sda5         306,536,328   312,576,704     6,040,377  82 Linux swap / Solaris
/dev/sda3    *    257,361,300   292,864,949    35,503,650   7 HPFS/NTFS
/dev/sda4         292,864,950   306,536,264    13,671,315   7 HPFS/NTFS


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8d399bc0

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   976,751,999   976,751,937   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="b0ffa8ed-9141-421d-b358-494bf8fe0af1" TYPE="ext3" 
/dev/sda3: UUID="2A70989D709870F5" LABEL="Preload" TYPE="ntfs" 
/dev/sda4: UUID="36DA800DDA7FC81F" LABEL="ServiceV002" TYPE="ntfs" 
/dev/sda5: UUID="ea541466-e4f6-45d9-a6f0-9a98fbeefd07" TYPE="swap" 
/dev/sdb1: LABEL="Elements" UUID="A0EE-A2DC" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/gabriel/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=gabriel)
/dev/sdb1 on /media/Elements type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

=========================== sda1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=b0ffa8ed-9141-421d-b358-494bf8fe0af1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=b0ffa8ed-9141-421d-b358-494bf8fe0af1

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		b0ffa8ed-9141-421d-b358-494bf8fe0af1
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=b0ffa8ed-9141-421d-b358-494bf8fe0af1 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		b0ffa8ed-9141-421d-b358-494bf8fe0af1
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=b0ffa8ed-9141-421d-b358-494bf8fe0af1 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		b0ffa8ed-9141-421d-b358-494bf8fe0af1
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=b0ffa8ed-9141-421d-b358-494bf8fe0af1 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		b0ffa8ed-9141-421d-b358-494bf8fe0af1
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=b0ffa8ed-9141-421d-b358-494bf8fe0af1 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		b0ffa8ed-9141-421d-b358-494bf8fe0af1
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=b0ffa8ed-9141-421d-b358-494bf8fe0af1 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		b0ffa8ed-9141-421d-b358-494bf8fe0af1
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=b0ffa8ed-9141-421d-b358-494bf8fe0af1 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		b0ffa8ed-9141-421d-b358-494bf8fe0af1
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=b0ffa8ed-9141-421d-b358-494bf8fe0af1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=ea541466-e4f6-45d9-a6f0-9a98fbeefd07 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   3.5GB: boot/grub/menu.lst
   3.5GB: boot/grub/stage2
   3.5GB: boot/initrd.img-2.6.27-11-generic
   3.5GB: boot/initrd.img-2.6.27-7-generic
   3.5GB: boot/initrd.img-2.6.27-9-generic
   3.5GB: boot/vmlinuz-2.6.27-11-generic
   3.5GB: boot/vmlinuz-2.6.27-7-generic
   3.5GB: boot/vmlinuz-2.6.27-9-generic
   3.5GB: initrd.img
   3.5GB: initrd.img.old
   3.5GB: vmlinuz
   3.5GB: vmlinuz.old

================================ sda3/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


```
What does it say to you?

---

### Post by caljohnsmith on 2009-02-08
For some reason the script was not able to identify your Vista sda4 partition as a complete Vista install, so you might have some trouble booting it. But the only way to find out is by trying, so how about first opening your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And then at the bottom add:
```
title Windows XP
root (hd0,2)
chainloader +1

title Windows Vista
root (hd0,3)
chainloader +1
```
Reboot, and please let me know exactly what happens when you try to boot XP and Vista from your Grub menu. We can work from there.

---

### Post by GabrielWolff on 2009-02-09
Great, thank you so much. It worked perfectly.

I rebooted, pressed esc, it gave me the options of booting the WIN partition, I did, and WIN started up.

Thank you! :)

Gabriel

---

### Post by caljohnsmith on 2009-02-09
That's great news, glad to hear that worked OK; cheers and enjoy Ubuntu and Windows. :)

---

