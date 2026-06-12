---
title: "grub problems"
date: 2006-08-10
forum: Desktop Environments
---

### Post by Illusionistx on 2006-08-10
after i installed dapper drake, by mbr was invalid and i kept getting the error 'hard disk boot record invalid' or something. 
i read a few posts on here, but none seemed to help get grub installed back to my mbr. 
what i could do though was boot with the live cd, then select boot from first hdd, then my grub loader would come up and i could boot into ubuntu or xp. 
i messed with that for a while, trying all the different suggested methds of fixing, and none worked. 
then i found something about GAG and tried it, it installed fine, only when i would select which OS to boot into it would always take me to the GRUB booter, from there i could boot into ubuntu, but everytime i tried to boot xp it would just keep loading grub. 
i think uninstalled GAG and, that fixed my mbr, and when i boot up it goes straight into grub.
however, i still cannot boot into xp, it just keeps going back to grub...
anyone have any more suggestions on how i can fix this? 
hope that isn't too confusing...
thanks

---

### Post by Illusionistx on 2006-08-10
more info: 
with Breezy i used to be able to mount my xp partition
since i installed dapper and by mbr got messed up or something i can't, and when i do dmesg | tail i get 
```

NTFS-fs warning (device hdc1): is_boot_sector_ntfs(): Invalid boot sector checksum.
NTFS-fs error (device hdc1): read_ntfs_boot_sector(): Primary boot sector is invalid.
NTFS-fs error (device hdc1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
NTFS-fs error (device hdc1): ntfs_fill_super(): Not an NTFS volume.

```

---

### Post by murataht on 2006-08-10
i think, you should check your partition with fdisk:

> sudo fdisk /dev/hda

and type "p" to see the partitions.

and type "q" to quit.

if there is no "*" infront of the windows partition, it is not activated for booting. and if there is a "*" in front of the linux partition, it is activated for booting. and i think this the case for you. (i maybe wrong, let me know. thanks).

maybe you can install grub this way:

# Run grub command to enter grub shell
>sudo grub

# Type in the root disk for grub, for example:

grub> root (hd0,1)

This is /dev/hda2 on my system

# Type the following command to install grub on /dev/hda: 
grub> setup (hd0).

# Last step, type quit.
grub> quit

The boot partition is where you put the boot files, normally newbies use only one partition that is mounted on /. Some advanced users store boot files in a separate partition and mount it under /boot. In that case, is the partition that is mounted under /boot the known-to-grub root partition.

NOTE: edited from: [http://www.debian-administration.org/articles/325](http://www.debian-administration.org/articles/325)

---

### Post by murataht on 2006-08-11
excuse me, but you have three hard disk???? 

hdc1 for windows xp???? (from the error message)

it is really odd....

---

### Post by Illusionistx on 2006-08-11
no, there is one hdd with 3 partitions. 
and xp is set to boot
and i already tried installing grub that way and it didn't work.

---

### Post by murataht on 2006-08-11
if you have hdd, and the error message is showing hdc??? do you think it is normal? it is looking for the right hard disk???

btw, do you have only one hard disk? and it is labeled hdd???

---

### Post by Illusionistx on 2006-08-11
> **murataht said:**
> if you have hdd, and the error message is showing hdc??? do you think it is normal? it is looking for the right hard disk???

btw, do you have only one hard disk? and it is labeled hdd???

maybe my last post wasn't clear enough.... 
hdd = harddrive, not the name of my harddrive
> **Illusionistx said:**
> 
no, there is one (1) hdd (harddrive): hdc 
my harddrive has 3 partitions: 
hdc1 = winxp
hdc2 = ubuntu
hdc3 = swap
and xp is set to boot
and i already tried installing grub that way and it didn't work.

i can boot into ubuntu fine, but from grub when i try to boot into xp it just keeps reloading grub

---

### Post by varean on 2006-08-11
Perhaps there is an issue with the grub.conf file itself.  Can you post the grub.conf file here so we can take a look?

---

### Post by Illusionistx on 2006-08-11
i'll have to do that later, i'm at work and wont be going back home until late tonight. 
but thanks, and i'll do that when i get home.

---

### Post by Illusionistx on 2006-08-11
hmm i don't have a grub.conf file. 
the only files in my /boot/grub folder are 
device.map
menu.lst
and the grub stage files

---

### Post by murataht on 2006-08-11
can you post the menu.lst here?

---

### Post by Illusionistx on 2006-08-11
```
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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=/dev/hdc2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdc2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdc2 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdc1
title		Microsoft Windows XP Professional
root		(hd0,0)
makeactive
chainloader	+1


```

---

### Post by Illusionistx on 2006-08-12
i haven't changed anything in it, and it used to work just fine. i don't know what happened. i think it might be a problem with my xp partition though because i can't even mount it or anything

---

### Post by Tomosaur on 2006-08-12
This is odd indeed. Try running 'sudo update-grub' in a terminal. It should rescan for operating systems and edit menu.lst to reflect what it finds. If WinXP is missing from the list after it's run, you may have a big problem. Backup your menu.lst file before running it though, just so you can get it back to normal later on.

---

### Post by Illusionistx on 2006-08-12
ok i tried that and it looks like my menu.lst is still the same. i'll reboot and see if i can boot into XP now.

<edit> rebooted and GRUB loaded, seleted win xp, then it started to load GRUB again. i noticed when it first comes up it says loading stage 1.5, but then after i select XP and it loads again it load stage 2.  deos that have anythign to do with anything? 

i already had GRUB installed then i upgraded to dapper and it reinstalled and that's when al of this happened. i'm thinking something happened to the my xp partition, because i can't mount it either...

---

### Post by Illusionistx on 2006-08-12
any more suggestions?

---

### Post by murataht on 2006-08-12
1) i noticed that in your menul.lst, it says you are using the /dev/hdc. but you told me that you have only one hard disk. so why the system is using the hdc? normally first hard disk is noted as /dev/hda, second one is /dev/hdb, and so on. or maybe you hooked your hard disk to the second ide, not the first one. have you messed up with your ide configuration recently? maybe this can give you some hint.

2) you also said you cant mount the windows partition, can you post the error message here. 

3) to be sure about your hard disk configuration, can you try:

sudo fdisk /dev/hdc (p for print the partition table, and q for quit)
and
sudo fdisk /dev/hda

and print the partition tabel here.  

hopefully those can give some hints to the problem...

Murat

---

### Post by Illusionistx on 2006-08-12
i'm on a laptop, and it's just like it was when i bought it. i do only have one harddrive and it's under hdc. 
i know that it works because everything worked fine in breezy.
there is no hda device.
```

chris@chris-laptop:~$ sudo mount /win
mount: wrong fs type, bad option, bad superblock on /dev/hdc1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

chris@chris-laptop:~$ sudo dmesg | tail
[17200134.768000] PCMCIA: socket dd24f028: *** DANGER *** unable to remove socket power
[17202304.180000] cs: pcmcia_socket0: voltage interrogation timed out.
[17202859.724000] spurious 8259A interrupt: IRQ7.
[17203612.732000] cs: pcmcia_socket0: cardbus cards are not supported.
[17203612.768000] PCMCIA: socket dd24f028: *** DANGER *** unable to remove socket power
[17218293.756000] printk: 80 messages suppressed.
[17218293.756000] NTFS-fs warning (device hdc1): is_boot_sector_ntfs(): Invalid boot sector checksum.
[17218293.756000] NTFS-fs error (device hdc1): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17218293.756000] NTFS-fs error (device hdc1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[17218293.756000] NTFS-fs error (device hdc1): ntfs_fill_super(): Not an NTFS volume.

```
```
chris@chris-laptop:~$ sudo fdisk /dev/hdc

The number of cylinders for this disk is set to 7296.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p

Disk /dev/hdc: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        4584    36820948+   7  HPFS/NTFS
/dev/hdc2            4585        7166    20739915   83  Linux
/dev/hdc3            7167        7296     1044225   82  Linux swap / Solaris

```

and to say it one more time, everything worked fine in 5.10 breezy. i had no problems with grub or mounting hdc1 my xp partition. all this occured when i formatted the two partitions and installed dapper from the desktop cd

---

### Post by Tomosaur on 2006-08-13
Wait a minute. 

Someone may need to clarify this, but aren't the first 63 'cylinders' reserved for boot files? This is my output of fdisk:

```

Disk /dev/hda: 163.9 GB, 163928604672 bytes
240 heads, 63 sectors/track, 21175 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1              63    11929679     5964808+  1c  Hidden W95 FAT32 (LBA)
/dev/hda2        11929680    74843999    31457160   83  Linux
/dev/hda3        74844000    75887279      521640   82  Linux swap / Solaris
/dev/hda4   *    75887280   320150879   122131800    7  HPFS/NTFS

```

Notice how the first partition starts on 63? I'm not sure what the implications of this are, but I just thought I'd point it out.

---

### Post by Illusionistx on 2006-08-13
there was another thread that started with the same problem i'm having now. grub wont boot into windows. so i did as suggested there, boot with xp cd and try fixmbr. well it didn't work. i don't even think it wrote anythign to the mbr because when i restarted it still loaded grub. and i'm still having the same problems. anyone know anything else i could possibly do?

---

### Post by Illusionistx on 2006-08-16
ok, i tried fixmbr again, and it still didn't work.
i booted into the repair console again and did fixmbr, and fixboot. 
now when i reboot i get the NTLDR is missing error
i read somewhere how to fix that and i tried to copy the ntldr files fromt he cd to my c:\ directoy, but i get Acess Denied error.  does anyone know what i can do from here?

---

### Post by murataht on 2006-08-16
I think it is a windows problem now. actually it is been a windows problem, i think. what about repair the xp with an xp installation disk? i don't know, but just a suggestion. good luck!!!

---

### Post by Illusionistx on 2006-08-17
yeah that's what i tried to do, with fixmbr and what all else. but i guess i'll either have to reinstall xp or just format that partition and use it for  something else, possibly anoher linux distro?

---

### Post by murataht on 2006-08-17
you should use it for another distro, or just run xp with xen or vmware in that partition. ;)

---

### Post by Illusionistx on 2006-08-17
what other distro would you recommend

---

### Post by murataht on 2006-08-18
it depends on your taste:
if you wanna try something difficult and wanna try learn more about linux inner mechanisms: gentoo, and lfs (linux from scratch).

if you want a fast one, not as difficult as gentoo, arch linux...

or, suse, maybe someday if SELD got famous, it won't hurt to know something about it, maybe job opportunities ... :) 

tons of others ...

---

### Post by Illusionistx on 2006-08-18
cool i'll look into those

---

