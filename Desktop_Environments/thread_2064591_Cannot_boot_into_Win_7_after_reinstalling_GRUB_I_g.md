---
title: "Cannot boot into Win 7 after reinstalling GRUB: I get &quot;Error 13&quot; (details below)"
date: 2012-09-29
forum: Desktop Environments
---

### Post by sankscan on 2012-09-29
My machine has 2 separate physical disks, one for each OS. Windows (sda) and Ubuntu Linux (sdb). My Windows disk had "Vista Business x64" and the linux disk has Ubuntu 12.04. I recently upgraded Vista to "Win 7 Pro x64" and as expected, it screwed with the MBR and GRUB was not coming up at boot up time. So, I reinstall GRUB and go through the whole 9 yards (Booting from live CD and mounting the boot partition, reinstalling GRUB). Please note that I installed GRUB only on 'sdb' and I changed the boot sequence (in BIOS) to pick 'sdb' as the first disk (because o/w GRUB will not come up). I did not install GRUB on 'sda' because I was afraid, it might screw up something.

I can see GRUB come up now on boot up with the menu options for 'Win 7' and 'Ubuntu'. Booting into Ubuntu is OK but when I choose the Windows, I get this error:

"Error 13: Invalid or unsupported executable format. Press any key to continue.....".

When I press a key, it takes me back to GRUB. Below are the steps that I followed from the link ([http://askubuntu.com/questions/88384/how-can-i-repair-grub-how-to-get-ubuntu-back-after-installing-windows](http://askubuntu.com/questions/88384/how-can-i-repair-grub-how-to-get-ubuntu-back-after-installing-windows)). Any clues how I can resurrect my m/c?

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x954b5a9b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   976771071   488384512    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ad2ea

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63    48821534    24410736   83  Linux
/dev/sdb2        48821535   244139804    97659135   83  Linux
/dev/sdb3       244139805   248043599     1951897+  82  Linux swap / Solaris
/dev/sdb4       248043600   976768064   364362232+  83  Linux

```

```
ubuntu@ubuntu:~$ sudo mount /dev/sdb1 /mnt
ubuntu@ubuntu:~$ cd /mnt/
ubuntu@ubuntu:/mnt$ ls
bin    dev   initrd.img      lib64       mnt   root  selinux  tmp  vmlinuz
boot   etc   initrd.img.old  lost+found  opt   run   srv      usr  vmlinuz.old
cdrom  home  lib             media       proc  sbin  sys      var

ubuntu@ubuntu:/mnt$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:/mnt$ sudo mount --bind /dev/pts /mnt/dev/pts
ubuntu@ubuntu:/mnt$ sudo mount --bind /proc /mnt/proc
ubuntu@ubuntu:/mnt$ sudo mount --bind /sys /mnt/sys
ubuntu@ubuntu:/mnt$
ubuntu@ubuntu:/mnt$
ubuntu@ubuntu:/mnt$
ubuntu@ubuntu:/mnt$ sudo chroot /mnt
root@ubuntu:/#
root@ubuntu:/#
root@ubuntu:/#
root@ubuntu:/# update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-3.2.0-26-generic
Found kernel: /boot/vmlinuz-3.2.0-25-generic
Found kernel: /boot/vmlinuz-3.2.0-24-generic
Found kernel: /boot/vmlinuz-3.2.0-23-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

root@ubuntu:/# grub-install /dev/sdb

Searching for GRUB installation directory ... found: /boot/grub
Installing GRUB to /dev/sdb as (hd1)...
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda
(hd1)    /dev/sdb

root@ubuntu:/# sudo grub-install --recheck /dev/sdb
sudo: unable to resolve host ubuntu
Probing devices to guess BIOS drives. This may take a long time.

Searching for GRUB installation directory ... found: /boot/grub
Installing GRUB to /dev/sdb as (hd1)...
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)    /dev/fd0
(hd0)    /dev/sda
(hd1)    /dev/sdb
root@ubuntu:/# exit
ubuntu@ubuntu:~$
ubuntu@ubuntu:~$
ubuntu@ubuntu:~$ sudo umount /mnt/dev/pts
ubuntu@ubuntu:~$ sudo umount /mnt/dev
ubuntu@ubuntu:~$ sudo umount /mnt/proc
ubuntu@ubuntu:~$ sudo umount /mnt/sys

ubuntu@ubuntu:~$
ubuntu@ubuntu:~$
ubuntu@ubuntu:~$
ubuntu@ubuntu:~$ sudo reboot
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%


```
Here's my menu.lst
```

&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&
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

#default        1
#Changed default to 1 by SS 03/06/12
default        1

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=c97eee3c-784b-4ce8-a9bf-a80f10378f31 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=c97eee3c-784b-4ce8-a9bf-a80f10378f31

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
# defoptions=quiet splash vga=799

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

#title Windows
#root

title        Windows 7 Pro x64
root        (hd0,0)
savedefault
makeactive
chainloader +1

# This is a divider to separate Ubuntu 
# from Windows

title           Ubuntu 12.04, kernel 3.2.0-31-generic
root            (hd1,0)
uuid            c97eee3c-784b-4ce8-a9bf-a80f10378f31
kernel          /boot/vmlinuz-3.2.0-31-generic root=UUID=c97eee3c-784b-4ce8-a9bf-a80f10378f31 ro quiet splash
initrd          /boot/initrd.img-3.2.0-31-generic
quiet
savedefault

title           Ubuntu 12.04, kernel 3.2.0-26-generic
root            (hd1,0)
uuid            c97eee3c-784b-4ce8-a9bf-a80f10378f31
kernel          /boot/vmlinuz-3.2.0-26-generic root=UUID=c97eee3c-784b-4ce8-a9bf-a80f10378f31 ro quiet splash
initrd          /boot/initrd.img-3.2.0-26-generic
quiet
savedefault

title           Ubuntu 12.04, kernel 3.2.0-26-generic (recovery mode)
uuid            c97eee3c-784b-4ce8-a9bf-a80f10378f31
kernel          /boot/vmlinuz-3.2.0-26-generic root=UUID=c97eee3c-784b-4ce8-a9bf-a80f10378f31 ro  single
initrd          /boot/initrd.img-3.2.0-26-generic

title        Ubuntu 12.04, memtest86+
root        (hd1,0)
uuid        c97eee3c-784b-4ce8-a9bf-a80f10378f31
kernel        /boot/memtest86+.bin
quiet

title        Ubuntu 12.04, kernel 3.2.0-24-generic
root        (hd1,0)
uuid        c97eee3c-784b-4ce8-a9bf-a80f10378f31
kernel        /boot/vmlinuz-3.2.0-24-generic root=UUID=c97eee3c-784b-4ce8-a9bf-a80f10378f31 ro quiet splash 
initrd        /boot/initrd.img-3.2.0-24-generic
quiet
savedefault

title        Ubuntu 12.04, kernel 3.2.0-24-generic (recovery mode)
uuid        c97eee3c-784b-4ce8-a9bf-a80f10378f31
kernel        /boot/vmlinuz-3.2.0-24-generic root=UUID=c97eee3c-784b-4ce8-a9bf-a80f10378f31 ro  single
initrd        /boot/initrd.img-3.2.0-24-generic

title        Ubuntu 11.10, kernel 2.6.32-33-generic
uuid        c97eee3c-784b-4ce8-a9bf-a80f10378f31
kernel        /boot/vmlinuz-2.6.32-33-generic root=UUID=c97eee3c-784b-4ce8-a9bf-a80f10378f31 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-33-generic
quiet

title        Ubuntu 11.10, kernel 2.6.32-33-generic (recovery mode)
uuid        c97eee3c-784b-4ce8-a9bf-a80f10378f31
kernel        /boot/vmlinuz-2.6.32-33-generic root=UUID=c97eee3c-784b-4ce8-a9bf-a80f10378f31 ro  single
initrd        /boot/initrd.img-2.6.32-33-generic

title        Ubuntu 11.10, memtest86+
root        (hd1,0)
uuid        c97eee3c-784b-4ce8-a9bf-a80f10378f31
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&
```

---

### Post by sankscan on 2012-09-29
Another interesting that I noted was as soon as I chose to boot from 'ubuntu' from GRUB, I see this message:

"Boot from (hd0,0) ext3, <uuid>"

I was wondering why is it booting from (hd0,0) which is the Windows disk and not from (hd0,1) which is my linux disk (check my menu.lst)???

---

### Post by oldfred on 2012-09-29
How did you get grub legacy into your system. Was that intentional? A few still do not like grub2, but I do. 
Grub legacy was last used on 9.04 and 9.10 was the first with grub2.

Error 13 is from grub legacy. menu.lst is from grub legacy. Legacy did not dual boot with Windows 7 well, as I remember we had to add boot stanzas manually, but I have forgotten most of grub legacy.

Best to convert back to grub2. This tool makes it easy to uninstall grub and reinstall grub2.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by sankscan on 2012-09-30
Thanks Fred! I never realized that grub was legacy. I did OK with it with 12.04LT and Win Vistax64. I'm going to give boot-repair a shot...Can't I re-install grub2 while I'm booted onto ubuntu? The procedure looks complicated and I'm afraid I might screw up! Just wondering! Has anyone gone through this before and if you can relate your experience, that will be great!

---

### Post by oldfred on 2012-09-30
If you are booted into your system, you can skip the chroot and just uninstall grub & reinstall grub-pc (grub2). But make sure your Internet connection is working as it has to download from repository.

chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

