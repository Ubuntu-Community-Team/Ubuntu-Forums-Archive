---
title: "Getting Grub Error 13"
date: 2009-02-17
forum: General Help
---

### Post by Twig E. Pottox on 2009-02-17
Help,  When I try to start XP on a dual drive dual boot machine I get Error 13 Invalid or unsupported executable drive.

Ubuntu starts and runs well. XP gets the above error

I installed  xp first on the master HDD drive and then Ubuntu 8.10 64 bit on the slave HDD of the same IDE Channel. the machine has A DVD Drive on a SATA Channel The Computer is a intel dual core 2.6Ghz with 4 GB Mem

The boot settings may have got corrupted when I put in another HDD on a SATA Channel. I have since removed that drive.

any suggestions will be appreciated.

MY /boot/grub/menu.lst is as follows:


## ## End Default Options ## 

title		Ubuntu 8.10, kernel 2.6.27-11-generic 
uuid		1b825619-f686-40c6-a153-07cce81c93a8 
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=1b825619-f686-40c6-a153-07cce81c93a8 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic 
quiet 

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode) 
uuid		1b825619-f686-40c6-a153-07cce81c93a8 
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=1b825619-f686-40c6-a153-07cce81c93a8 ro  single 
initrd		/boot/initrd.img-2.6.27-11-generic 

title		Ubuntu 8.10, kernel 2.6.27-9-generic 
uuid		1b825619-f686-40c6-a153-07cce81c93a8 
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=1b825619-f686-40c6-a153-07cce81c93a8 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic 
quiet 

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode) 
uuid		1b825619-f686-40c6-a153-07cce81c93a8 
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=1b825619-f686-40c6-a153-07cce81c93a8 ro  single 
initrd		/boot/initrd.img-2.6.27-9-generic 

title		Ubuntu 8.10, kernel 2.6.27-7-generic 
uuid		1b825619-f686-40c6-a153-07cce81c93a8 
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1b825619-f686-40c6-a153-07cce81c93a8 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic 
quiet 

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) 
uuid		1b825619-f686-40c6-a153-07cce81c93a8 
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1b825619-f686-40c6-a153-07cce81c93a8 ro  single 
initrd		/boot/initrd.img-2.6.27-7-generic 

title		Ubuntu 8.10, memtest86+ 
uuid		1b825619-f686-40c6-a153-07cce81c93a8 
kernel		/boot/memtest86+.bin 
quiet 

### END DEBIAN AUTOMAGIC KERNELS LIST 

# This is a divider, added to separate the menu items below from the Debian 
# ones. 
title		Other operating systems: 
root 


# This entry automatically added by the Debian installer for a non-linux OS 
# on /dev/sdb1 
title		Microsoft Windows XP Professional 
root		(hd1,0) 
savedefault 
makeactive 
map		(hd0) (hd1) 
map		(hd1) (hd0) 
chainloader	+1

---

### Post by caljohnsmith on 2009-02-17
In order to get a clearer picture of your setup, how about downloading the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by Twig E. Pottox on 2009-02-17
Thanks for the instructions, I think I followed them right.-



```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x01f501f5

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   102,398,309   102,398,247   7 HPFS/NTFS
/dev/sda2         102,398,310   625,137,344   522,739,035   7 HPFS/NTFS


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x75cd4182

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    39,070,079    39,070,017  83 Linux
/dev/sdb2         302,809,185   312,576,704     9,767,520  82 Linux swap / Solaris
/dev/sdb3          39,070,080   302,809,184   263,739,105  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="9480DE4680DE2E8C" TYPE="ntfs" 
/dev/sda2: UUID="B8D806BDD8067A40" LABEL="New Volume" TYPE="ntfs" 
/dev/sdb1: UUID="1b825619-f686-40c6-a153-07cce81c93a8" TYPE="ext3" 
/dev/sdb2: UUID="34b724bb-27ab-482f-ae18-58d1602ff3f6" TYPE="swap" 
/dev/sdb3: UUID="2042bba5-02c2-44af-a377-c559f156e275" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
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
/dev/sdb3 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/steve/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=steve)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn


=========================== sdb1/boot/grub/menu.lst: ===========================

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
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# kopt=root=UUID=1b825619-f686-40c6-a153-07cce81c93a8 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=1b825619-f686-40c6-a153-07cce81c93a8

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
uuid		1b825619-f686-40c6-a153-07cce81c93a8
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=1b825619-f686-40c6-a153-07cce81c93a8 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		1b825619-f686-40c6-a153-07cce81c93a8
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=1b825619-f686-40c6-a153-07cce81c93a8 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		1b825619-f686-40c6-a153-07cce81c93a8
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=1b825619-f686-40c6-a153-07cce81c93a8 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		1b825619-f686-40c6-a153-07cce81c93a8
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=1b825619-f686-40c6-a153-07cce81c93a8 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		1b825619-f686-40c6-a153-07cce81c93a8
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1b825619-f686-40c6-a153-07cce81c93a8 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		1b825619-f686-40c6-a153-07cce81c93a8
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1b825619-f686-40c6-a153-07cce81c93a8 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		1b825619-f686-40c6-a153-07cce81c93a8
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
UUID=1b825619-f686-40c6-a153-07cce81c93a8 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc3
UUID=2042bba5-02c2-44af-a377-c559f156e275 /home           ext3    relatime        0       2
# /dev/sdc2
UUID=34b724bb-27ab-482f-ae18-58d1602ff3f6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  16.9GB: boot/grub/menu.lst
  16.9GB: boot/grub/stage2
  17.0GB: boot/initrd.img-2.6.27-11-generic
  16.9GB: boot/initrd.img-2.6.27-7-generic
  17.0GB: boot/initrd.img-2.6.27-9-generic
  17.0GB: boot/vmlinuz-2.6.27-11-generic
  16.9GB: boot/vmlinuz-2.6.27-7-generic
  17.0GB: boot/vmlinuz-2.6.27-9-generic
  17.0GB: initrd.img
  17.0GB: initrd.img.old
  17.0GB: vmlinuz
  17.0GB: vmlinuz.old
```

---

### Post by caljohnsmith on 2009-02-17
I think it's worth mentioning that you have Grub installed to the MBR (Master Boot Record) of your Windows sda drive, yet Grub looks on the Ubuntu sdb drive for its boot files. That means your drives are dependent on each other right now for booting, so if anything happens to either one (or if something happens to the Ubuntu partition), you won't be able to boot Ubuntu or Windows. If you are OK with that, that's fine, but I would recommend installing Grub to the MBR of your sdb Ubuntu drive, restore a Windows MBR to your sda Windows drive, set your BIOS to boot the Ubuntu sdb drive, and you should be all set;  your current Grub entry for Windows should work just fine, so you should be able to boot Ubuntu or Windows from your Grub menu. That way your drives will be independent of each other as far as booting is concerned, so if something happens to one of the drives, you should be able to boot the OS on the other drive. If that sounds good to you, how about doing:
```
sudo grub
grub> root (hd1,0)
grub> setup (hd1)
grub> quit
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
Reboot, set your BIOS to boot the sdb Ubuntu drive, and if all goes well you should be able to boot Ubuntu or Windows from your Grub menu. Let me know how it goes or if you run into problems.

---

### Post by Twig E. Pottox on 2009-02-17
Thanks again, I did like you said as it makes sense -but got errors as follows:


note: when it comes to the command line [I]'m weak at best so any minor context nuances are lost on me at this point.
When I changed the boot disk to the ubuntu disk  in BIOS I got "error loading Operating system" message before it got to the grub so I changed it back to get buntu back up.  any Ideas? 



```


steve@base26duo:~$ sudo grub
[sudo] password for steve: 
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> root (hd1,0)
grub> setup (hd1)
grub> quit
sudo apt-get install lilo
sudo lilo -M /root (hd1,0)d
ev/sda mbrgrub> grub> setup (hd1)

Error 27: Unrecognized command
grub> grub> quit

Error 27: Unrecognized command
grub> sudo apt-get install lilo

Error 27: Unrecognized command
grub> 
```

---

### Post by Twig E. Pottox on 2009-02-18
Thanks again caljohnsmith. Your instructions fixed the problem. I was taking the command line instructions too literally at first. after rethinking them and entering them one at a time it took without an error, I changed the BIOs Settings and all is working as it should.

---

### Post by caljohnsmith on 2009-02-18
Glad to hear you figured out the problem, Twig, and that it's all working OK now; cheers and enjoy your dual-boot Ubuntu and Windows setup. :)

---

