---
title: "GRUB Error 17 and 15"
date: 2009-02-14
forum: General Help
---

### Post by Deldo on 2009-02-14
Hi

After a half an year with Ubuntu I decided to install XP again along with a new fresh Ubuntu installation.
I installed XP as I normally would. But when I restart the computer normally the first time (the installation is not yet complete), I got this message on the screen:

"GRUB loading stage 1.5
Please wait
Error 17"

I reinstalled Ubuntu and got the same message. Then I installed Ubuntu again and now it is working. I have done this to times and with the same result. I have also noticed that I got both error 17 and 15, if this can help.

What is wrong? And most important, how can I fix it?

---

### Post by netgooroo on 2009-02-14
I get this same error when booting. what is the fix for error 17?

---

### Post by caljohnsmith on 2009-02-14
Netgooroo, in order to get a clearer picture of your setup, how about booting your Ubuntu Live CD (the Ubuntu install CD), download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to the Live CD desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your Grub error 17 problem might be.

---

### Post by Deldo on 2009-02-14
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

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

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 60.0 Gb, 60011642880 byte
255 heads, 63 sectors/track, 7296 cylinders, i alt 117210240 sektorer
Units = sektorer of 1 * 512 = 512 bytes
Disk identifier: 0xd53d826f

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   112,326,479   112,326,417  83 Linux
/dev/sda2         112,326,480   117,210,239     4,883,760   5 Extended
/dev/sda5         112,326,543   117,210,239     4,883,697  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="5f9d863c-8323-48a1-9100-c3cce0c40f4a" TYPE="ext3" 
/dev/sda5: UUID="24a6b137-7504-4183-a57f-17f8426b73d0" TYPE="swap" 

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
gvfs-fuse-daemon on /home/rune/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=rune)

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
# kopt=root=UUID=5f9d863c-8323-48a1-9100-c3cce0c40f4a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=5f9d863c-8323-48a1-9100-c3cce0c40f4a

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
uuid		5f9d863c-8323-48a1-9100-c3cce0c40f4a
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=5f9d863c-8323-48a1-9100-c3cce0c40f4a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		5f9d863c-8323-48a1-9100-c3cce0c40f4a
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=5f9d863c-8323-48a1-9100-c3cce0c40f4a ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		5f9d863c-8323-48a1-9100-c3cce0c40f4a
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=5f9d863c-8323-48a1-9100-c3cce0c40f4a ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		5f9d863c-8323-48a1-9100-c3cce0c40f4a
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=5f9d863c-8323-48a1-9100-c3cce0c40f4a ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		5f9d863c-8323-48a1-9100-c3cce0c40f4a
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=5f9d863c-8323-48a1-9100-c3cce0c40f4a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=24a6b137-7504-4183-a57f-17f8426b73d0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  12.4GB: boot/grub/menu.lst
  12.4GB: boot/grub/stage2
  12.3GB: boot/initrd.img-2.6.27-11-generic
  12.4GB: boot/initrd.img-2.6.27-7-generic
  12.4GB: boot/vmlinuz-2.6.27-11-generic
  12.4GB: boot/vmlinuz-2.6.27-7-generic
  12.3GB: initrd.img
  12.4GB: initrd.img.old
  12.4GB: vmlinuz
  12.4GB: vmlinuz.old
```

---

### Post by caljohnsmith on 2009-02-14
Deldo, when you reinstalled Windows, did you change the partition scheme of your HDD at all? I would think you probably did in order to install Windows, and if so, that would have been the cause of your Grub error 17. For future reference, you can usually fix it by following these instructions:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Deldo on 2009-02-14
The partition scheme?
I don't know what that is. But I will read the guide, if I can.

---

### Post by Deldo on 2009-02-17
Can anyone tell me how I can repair this?

---

### Post by caljohnsmith on 2009-02-17
According to the script results that you posted, Deldo, you only have Ubuntu installed to your 60 GB sda drive. So if Windows was on there before, it isn't any longer. If you want Windows and Ubuntu on that same HDD, how about reinstalling Windows, and then when you go to reinstall Ubuntu afterwards, choose the "manual" partition option in the Ubuntu installer. There you can shrink the Windows partition (if necessary) and set up your Ubuntu partitions. You might find this guide helpful:

[http://mywebsite.bigpond.net.au/dfelderh/linuxmaniac/p23.html](http://mywebsite.bigpond.net.au/dfelderh/linuxmaniac/p23.html)

And if you still get Grub errors after following the above tutorial, post the output of the Boot Info Script again before you try reinstalling yet again.

---

### Post by Deldo on 2009-02-18
caljohnsmith, if I install Windows again, I will proberly still get the GRUB error. So I don't see a point in installing Windows again, if I don't change something before or under the installing.
I have installed the Partition Editor on Ubuntu, can I change anything with this? Also when I install Windows I can install it on the entire HDD and with (I think) 2 partitions. Can this help somehow?

---

### Post by caljohnsmith on 2009-02-18
If you want to make a partition for Windows, you would have to do it from the Live CD because you can't be in your Ubuntu install and shrink it at the same time. So if you run the partition editor from the Live CD, try shrinking your sda1 Linux partition from the end to create space for Windows, then create a new primary NTFS partition for Windows. After that, try installing Windows to that partition. If that works and you can boot into Windows, you can restore Grub via these directions:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Deldo on 2009-02-18
Windows erases everything when I install it, so can I use Wubi to install Ubuntu and have the dual boot when I start my computer?
Or do I need to recover GRUB after my Windows-installation?

---

### Post by caljohnsmith on 2009-02-18
Sure, give Wubi a try, because then you shouldn't need to worry about restoring Grub.

---

### Post by wildman4god on 2009-02-18
> **Deldo said:**
> Windows erases everything when I install it, so can I use Wubi to install Ubuntu and have the dual boot when I start my computer?
Or do I need to recover GRUB after my Windows-installation?

use this method only if your absolutly sure your ubuntu install is gone, try to recover grub first (i had the same problem installing xp after ubuntu was already installed) this site will help you recover grub:

[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

I wouldn't use wubi mainly because the hard drive proformance isn't as good, if you need to do a new dual-boot, install windows first (it should already be if it wiped out you existing ubuntu install) the just pop in the ubuntu live cd and dual boot like normal (ubuntu dual boots very well with xp) when installing ubuntu the partitioner sets up and make sure "guide mode - use free space" option is selected and you'll see a slider that shows windows on one side and ubuntu on the other, use the slider to select the size you want for ubuntu, DO NOT make the windows partion any smaller than what is starts out as also make sure you defrag the hard drive first or a single piece of windows data moved out on the end of the hard drive will prevent ubuntu from having any usable hard drive space. good luck.

---

### Post by Deldo on 2009-02-18
I tried to install windows again by changing how to install it:
1. On entire HD.
2. With 2 partitions.
3. On first partition.
4. On entire HD with on partition.

I still got the error 17 message. It comes just before the OS installation of Windows. 

wildman4god, I will try out the guide. But to your answer, I can't install Windows, so untill I can install WinXP, I can't do as you say. :-/

---

### Post by Deldo on 2009-02-18
I have now tried it out. And when I entered grub in a terminal and wrote "root (hd0,0)" and "setup (hd0)", I got this message: "Error 17: Cannot mount selected partition"

Edit: I found out what to do. I reinstalled GRUB, typed "find /boot/grub/stage1" in a terminal and got the answer (hd0,6).
So this is what I did:
sudo grub
> root (hd0,6)
> setup (hd0)
After that a little process started and finished. 
"Probing devices to guess BIOS drives. This may take a long time."

This is where I stand now.

---

### Post by wildman4god on 2009-02-18
> **Deldo said:**
> I have now tried it out. And when I entered grub in a terminal and wrote "root (hd0,0)" and "setup (hd0)", I got this message: "Error 17: Cannot mount selected partition"

Edit: I found out what to do. I reinstalled GRUB, typed "find /boot/grub/stage1" in a terminal and got the answer (hd0,6).
So this is what I did:
sudo grub
> root (hd0,6)
> setup (hd0)
After that a little process started and finished. 
"Probing devices to guess BIOS drives. This may take a long time."

This is where I stand now.

okay, so did the grub recover work? did you restart and see any error?

---

### Post by wildman4god on 2009-02-18
If you still have problems restoring grub visit this site: 

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17)

it has a lot of grub error 17 help advise including a very small grub boot disk to help with grub problems.

---

### Post by Deldo on 2009-02-19
I'll try to use Super GRUB Disk and see what happens. 
I can't understand why the error 17 comes up when Windows Installer delete the disk and install Windows on it.

Edit: When I install Windows and it copies files to the harddisk, PowerQuest PQImage finds an error 116, if this can help anything.

---

### Post by wildman4god on 2009-02-19
if your are doing a complete reinstall make sure you format the entire disk first, that should make the grub errors go away, I like to boot ubuntu into live cd and use gparted to format the entire drive.

---

### Post by Deldo on 2009-02-19
I have installed Windows now. Finally. I installed Windows as I use to and was stock again when the OS should install. So I used Super GRUB Disk to start Windows and it helped. The installation became complete. So my question is now. Can I use my Ubuntu 8.10 Live CD to install Ubuntu without deleting Windows or should I use Wubi?

---

### Post by wildman4god on 2009-02-20
you can use either, wubi will guarantee that you won't accidentally remove windows but hard drive performance will be slightly slower that normal. dual booting is not that hard when you go to install just select the guided use free space option which will present you with a slider to re size partitions, you'll see windows on one side of the slider and ubuntu on the other side, select the size you want for ubuntu, don't make the windows partition any smaller than what it starts out as, you'll ruin your windows install. this site gives a step by step detail account of it: 

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

good luck.

---

### Post by Deldo on 2009-02-21
I tried with the Live CD and this came up.
I have shorted the message a little bit, but it goes like this:
"The partition can only be resized by converting to FAT16. If Windows is installed you have to install the MS Windows boot loader again."

Is this a problem?

---

### Post by wildman4god on 2009-02-21
that depends, when you resized the windows partition did you make it smaller or larger than what the partitioner started it out as?

if you made the partition smaller then yes thats a problem, if you made it bigger than no, ubuntu will replace the MS Windows boot loader with grub, which can boot both.

---

### Post by Deldo on 2009-02-24
It now works. Thanks for everything.

---

