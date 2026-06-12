---
title: "GRUB not showing windows after editing menu.lst"
date: 2011-03-31
forum: Desktop Environments
---

### Post by rcatank on 2011-03-31
Guys, 


Before flaming - I did search didn't find something specific to my hard drive setup (meaning partitions), so I thought someone could just tell me the right parameters without the flaming.


While GRUB Loads, I do not see Windows 7 as an option listed, even after editing in the menu.lst


MENU.LST
```

## ## End Default Options ##

title		Ubuntu 10.04.2 LTS, kernel 2.6.32-30-generic
uuid		5834da8e-4d70-441f-919f-8f21c711e6ec
kernel		/boot/vmlinuz-2.6.32-30-generic root=UUID=5834da8e-4d70-441f-919f-8f21c711e6ec ro quiet splash 
initrd		/boot/initrd.img-2.6.32-30-generic

title		Ubuntu 10.04.2 LTS, kernel 2.6.32-30-generic (recovery mode)
uuid		5834da8e-4d70-441f-919f-8f21c711e6ec
kernel		/boot/vmlinuz-2.6.32-30-generic root=UUID=5834da8e-4d70-441f-919f-8f21c711e6ec ro  single
initrd		/boot/initrd.img-2.6.32-30-generic

title		Ubuntu 10.04.2 LTS, kernel 2.6.32-28-generic
uuid		5834da8e-4d70-441f-919f-8f21c711e6ec
kernel		/boot/vmlinuz-2.6.32-28-generic root=UUID=5834da8e-4d70-441f-919f-8f21c711e6ec ro quiet splash 
initrd		/boot/initrd.img-2.6.32-28-generic

title		Ubuntu 10.04.2 LTS, kernel 2.6.32-28-generic (recovery mode)
uuid		5834da8e-4d70-441f-919f-8f21c711e6ec
kernel		/boot/vmlinuz-2.6.32-28-generic root=UUID=5834da8e-4d70-441f-919f-8f21c711e6ec ro  single
initrd		/boot/initrd.img-2.6.32-28-generic

title		Chainload into GRUB 2
root		5834da8e-4d70-441f-919f-8f21c711e6ec
kernel		/boot/grub/core.img

title		Ubuntu 10.04.2 LTS, memtest86+
uuid		5834da8e-4d70-441f-919f-8f21c711e6ec
kernel		/boot/memtest86+.bin


### END DEBIAN AUTOMAGIC KERNELS LIST
title		Windows 7
rootnoverify	(hd0,3)
chainloader	+1

```


And here is fdisk -l

sda1 is where Ubuntu is running
sda3 is where Windows 7 is running

And I know Windows 7 is there, because I booted into it before reinstalling GRUB on the MBR.


```

root@knight:/home/tank# fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001ea6b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3916    31454246   83  Linux
/dev/sda2   *        3917        3929      102400    7  HPFS/NTFS
/dev/sda3            3929       58662   439641088    7  HPFS/NTFS
/dev/sda4           58662       60802    17185793    5  Extended
/dev/sda5           58662       60802    17185792   82  Linux swap / Solaris


```

Thanks

---

### Post by rcatank on 2011-03-31
```

## ## End Default Options ##

title        Ubuntu 10.04.2 LTS, kernel 2.6.32-30-generic
uuid        5834da8e-4d70-441f-919f-8f21c711e6ec
kernel        /boot/vmlinuz-2.6.32-30-generic root=UUID=5834da8e-4d70-441f-919f-8f21c711e6ec ro quiet splash 
initrd        /boot/initrd.img-2.6.32-30-generic

title        Windows 7
rootnoverify    (hd0,3)
chainloader    +1

### END DEBIAN AUTOMAGIC KERNELS LIST

```



So I decided to see if even if I drastically change the menu, will it see the changes when i boot up my machine.

And actually.. it did nothing. When I boot up, I still see Ubuntu first,  and Recovery, Mem86+ options and all that. The new changes did not  apply at all. 

This concludes to me that GRUB is not installed to /boot/grub/ It's gone somewhere else... So where do I edit the Menu now?

---

### Post by coffeecat on 2011-03-31
Three points.

* - If you are running Ubuntu 10.04, then you will have grub 2 unless you upgraded from a version prior to 9.10. Grub 2 doesn't use menu.lst, which is probably why editing it makes no difference. The older legacy grub uses menu.lst

* - Your Windows 7 probably boots from sda2, not sda3. Partition sda2 is about 100MB and is probably the W7 boot partition.

* - Legacy grubspeak for sda3 is (hd0,2) not (hd0,3) so even if your menu.lst was used, you wouldn't have been able to boot Windows with that stanza. Legacy grubspeak for sda2 is (hd0,1) but, confusingly, grub 2 refers to sda2 as (hd0,2). Clear? :)

I think the best thing is if you run the boot script in Ubuntu, here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Post the RESULTS.txt file in code tags and we can see what's what, and how to proceed.

The answer may as simple as running 'sudo update-grub' to regenerate grub2's grub.cfg. You might want to try that anyway. But if that doesn't work, there are several reasons why grub 2 doesn't detect Windows and the output of the boot script may tell us why.

---

### Post by rcatank on 2011-04-03
@CoffeeCat


You have been 100% right so far. I did run the boot script below, and sda2 is the Windows 7 system boot - so I would need to point the script there.

So speaking of script or menu.lst - where do I modify the menu's? I also updated grub, and it overwrote to /boot/grub/menu.lst again. But, I thought you said Grub2 doesn't use menu.lst file......

```

root@knight:/home/tank/Downloads# sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.32-30-generic
Found kernel: /boot/vmlinuz-2.6.32-28-generic
Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

```


And here are my results of the Boot Script - It's pretty long.

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Boot file info:     Grub 2 in the file /mbr.bin looks at sector 1 of the 
                       same hard drive for core.img, but core.img can not be 
                       found at this location.
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    62,910,539    62,908,492  83 Linux
/dev/sda2    *     62,912,512    63,117,311       204,800   7 HPFS/NTFS
/dev/sda3          63,117,312   942,399,487   879,282,176   7 HPFS/NTFS
/dev/sda4         942,401,534   976,773,119    34,371,586   5 Extended
/dev/sda5         942,401,536   976,773,119    34,371,584  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        5834da8e-4d70-441f-919f-8f21c711e6ec   ext4                                     
/dev/sda2        2E62088F62085DC9                       ntfs       System Reserved               
/dev/sda3        184E0ECB4E0EA21C                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        f49e354e-c37d-4f63-a155-2cd889a675b2   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)


=========================== sda1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		3

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
# kopt=root=UUID=5834da8e-4d70-441f-919f-8f21c711e6ec ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=5834da8e-4d70-441f-919f-8f21c711e6ec

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

title		Ubuntu 10.04.2 LTS, kernel 2.6.32-30-generic
uuid		5834da8e-4d70-441f-919f-8f21c711e6ec
kernel		/boot/vmlinuz-2.6.32-30-generic root=UUID=5834da8e-4d70-441f-919f-8f21c711e6ec ro quiet splash 
initrd		/boot/initrd.img-2.6.32-30-generic


### END DEBIAN AUTOMAGIC KERNELS LIST
# This is a divider, added to separate the menu items below from the Debian
# ones.
title	 OTHER OPERATING SYSTEM
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4

title	 Windows 7
root	 (hd0,3)
savedefault
makeactive
chainloader	+1

=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 5834da8e-4d70-441f-919f-8f21c711e6ec
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 5834da8e-4d70-441f-919f-8f21c711e6ec
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 5834da8e-4d70-441f-919f-8f21c711e6ec
	linux	/boot/vmlinuz-2.6.32-30-generic root=UUID=5834da8e-4d70-441f-919f-8f21c711e6ec ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 5834da8e-4d70-441f-919f-8f21c711e6ec
	echo	'Loading Linux 2.6.32-30-generic ...'
	linux	/boot/vmlinuz-2.6.32-30-generic root=UUID=5834da8e-4d70-441f-919f-8f21c711e6ec ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 5834da8e-4d70-441f-919f-8f21c711e6ec
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=5834da8e-4d70-441f-919f-8f21c711e6ec ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 5834da8e-4d70-441f-919f-8f21c711e6ec
	echo	'Loading Linux 2.6.32-28-generic ...'
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=5834da8e-4d70-441f-919f-8f21c711e6ec ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 5834da8e-4d70-441f-919f-8f21c711e6ec
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 5834da8e-4d70-441f-919f-8f21c711e6ec
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=5834da8e-4d70-441f-919f-8f21c711e6ec /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f49e354e-c37d-4f63-a155-2cd889a675b2 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


   2.9GB: boot/grub/core.img
   3.1GB: boot/grub/grub.cfg
   3.3GB: boot/grub/menu.lst
   2.9GB: boot/initrd.img-2.6.32-28-generic
   2.9GB: boot/initrd.img-2.6.32-30-generic
   2.9GB: boot/vmlinuz-2.6.32-28-generic
   2.9GB: boot/vmlinuz-2.6.32-30-generic
   2.9GB: initrd.img
   2.9GB: initrd.img.old
   2.9GB: vmlinuz
   2.9GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb 

```

---

### Post by coffeecat on 2011-04-03
> **rcatank said:**
> I also updated grub, and it overwrote to /boot/grub/menu.lst again. But, I thought you said Grub2 doesn't use menu.lst file......


You're quite right - it updated menu.lst. And I'm quite right - Grub2 doesn't use menu.lst. :)

The problem is that you seem to have a mixture of legacy grub and grub2 on your system. Legacy grub has its own update-grub script which is quite different and I guess legacy grub's update-grub is being run.

You may need to purge legacy grub before we can think about getting Windows in your grub menu. It's interesting that there's no Windows entry in your grub2 grub.cfg, and quite how you have a grub.cfg without a grub2 update-grub is beyond me. I'll have a think about this, but in the meantime some questions.

Have a look in /usr/sbin/update-grub. Is it about 1500 lines long? That's the legacy version. Or is it 3 lines long? That's the grub2 version.

Is your system one upgraded from pre-Karmic? I can see no other way you could have legacy grub, unless you tried to downgrade grub and only half-succeeded.

I see from your update-grub output that you were running as root in the terminal. You don't need to use sudo if you are running a root terminal.

---

### Post by Quackers on 2011-04-03
I see that it is noted in sda1 that core.img can not be found at the specified location.
Have you re-installed grub at some time, maybe using an old guide?
I would agree with coffeecat in that I would purge both grub legacy and grub2 then re-install grub2. There doesn't appear to be a problem with any of Windows' boot files so grub2 once purged and re-installed should have no problem picking it up.
You do not have a separate boot partition (for Ubuntu) so the instructions in the guide below are more simple to follow. 
If you scroll down to the "Purge & Reinstall without Chroot" section the details are there.
If you have any problems or questions just ask. It is better to get it right first time if possible :wink:
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by oldfred on 2011-04-03
I have to agree with coffeecat that it would be best to uninstall old grub. The best way is this, see note that you do not have to have liveCD if you can boot into your install. Also while both are uninstalled you will not be able to reboot until grub2 is reinstalled.

chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

You entry for grub legacy is not pointing to the correct partition. Grub legacy counts partitions starting at 0 and your win7 boot partition is sda2 so you have to use (hd0,1). And for whatever reason root did not work with win7 usually and you have to use rootnoverify.
rootnoverify  (hd0,1)
But grub2's osprober will autofind the correct entry for grub2's grub.cfg menu so that is moot.

---

### Post by rcatank on 2011-04-04
> **coffeecat said:**
> 

Have a look in /usr/sbin/update-grub. Is it about 1500 lines long? That's the legacy version. Or is it 3 lines long? That's the grub2 version.


this is like 1500 lines long

> 
Is your system one upgraded from pre-Karmic? I can see no other way you could have legacy grub, unless you tried to downgrade grub and only half-succeeded.


I did a fresh install of 10.04 then.... Loaded Windows 7.. Then loaded GRUB.. apparently to your conclusion it was both GRUB and GRUB2... lol

---

### Post by rcatank on 2011-04-04
> **oldfred said:**
> 

chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)


Before I start purging stuff.. Are there different guides to Purge GRUB and GRUB2? OR 1 Guide Fits both?

---

### Post by oldfred on 2011-04-05
drs305's commands remove both and reinstall one. You can actually reinstall either depending on what you want but we recommend reinstall grub2 which is named grub-pc in the repository. 

When both are uninstalled you cannot reboot, do make sure you have a good internet connection as it will download the grub2 packages and install them. If download does not work you will have problems.

---

### Post by coffeecat on 2011-04-05
> **rcatank said:**
> this is like 1500 lines long

That's the legacy grub update-grub script.

> **rcatank said:**
> I did a fresh install of 10.04 then.... Loaded Windows 7.. **Then loaded GRUB**.. apparently to your conclusion it was both GRUB and GRUB2... lol

You must have installed legacy grub from the package manager. There is no other way it could have got onto your system if you were doing a fresh install of 10.04.

Follow oldfred's directions in the previous post and you'll be fine.

---

### Post by rcatank on 2011-04-08
Thanks to coffeecat, Quackers, and oldfred. All what you have said has worked. 

I did end up purging both GRUB and GRUB2 successfully while in Ubuntu off the HDD (not live disc). 

Installed GRUB2, Did a update-grub, and walla.. Win 7 comes up as an option automagically thanks to the OS Prober. 

Now I have to say, I don't like how every time I run update-grub, it overwrites my modified grub.cfg file. 

Startup Manager is good at putting a GUI for viewing the options, and may be tweaking a few things. But, I cannot edit the number of Options I do want present with w/e extra parameters. 

Any suggestions? To not manually change grub.cfg, and running into overwrite issues with update-grub command?

Thanks again all.:popcorn:

---

### Post by coffeecat on 2011-04-08
I'm glad it's sorted.

You can't stop grub.cfg being overwritten every time update-grub is run, but you do have ways of controlling what goes into grub.cfg by means of the files in /etc/grub.d/. For instance, in my main install I don't want os-prober to autodetect other operating systems - I want my own custom entries. So I've made /etc/grub.d/30_os-prober non-executable so that os-prober is not run and put my custom entries in /etc/grub.d/40_custom.

But that barely scratches the surface of how customisable  grub2 can be. Here are a couple of links for starters:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Perhaps oldfred and Quackers may have some other links for you.

---

### Post by oldfred on 2011-04-08
I manually did customization like coffeecat using a lot of info from drs305 who have several threads with lots of grub2 info. But there are some newer gui tools that I have not used but some including drs305 recommend as alternatives for at least some customization.


Link with several of links below:
How to edit bootloader? Feb 2011
[http://ubuntuforums.org/showthread.php?t=1694681](http://ubuntuforums.org/showthread.php?t=1694681)

HOWTO: Grub Customizer 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)
A easy way to remove the amount of kernels is to install Ubuntu tweak:
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

How to: Create a Customized GRUB2 Screen that is Maintenance Free.
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

OR Partial Custom menu:
I used drs305's command to limit ubuntu entries to two, turned off os-prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two, also hiding of windows recovery partition
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober

One way to fix the descriptions is to move the windows entries to 40_custom and edit at will.

Copy the windows entries from this:
gedit /boot/grub/grub.cfg
Copy them to and edit only titles:
gksudo gedit /etc/grub.d/40_custom
Then do:
sudo update-grub

Another way:
Total Custom menu:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)
[http://ubuntuforums.org/showthread.php?t=1483827](http://ubuntuforums.org/showthread.php?t=1483827)

---

### Post by Halfling Rogue on 2011-12-27
Hey guys, have a similar problem and some worrying terminal feedback.

I followed the instructions at [http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony) to set up 64-bit Windows 7 Home Premium and 64-bit Ubuntu 10.04 on a Fujitsu Lifebook.

Installation and partitioning seemed to go well. The current disk setup is:

```
sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x68a8aa84

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6527    52427103+   7  HPFS/NTFS
/dev/sda2            6528       13054    52428127+  83  Linux
/dev/sda3           13055       13315     2096482+  82  Linux swap / Solaris
/dev/sda4           13316       38913   205615935    7  HPFS/NTFS
```


But Windows 7 (sda1) isn't showing up in GRUB upon boot. (sda4 is the ntfs storage partition for both OSes to access.)

When I tried to update GRUB as per the instructions here, I got "error: cannot seek `/dev/sda'."

My searches are telling me that "cannot seek 'dev/sda'." is a bad message to be getting. But sda1 is listed as the boot partition and the computer is starting up fine, so it must know the partition is *there*. Help?

**Edit:** /usr/sbin/grub-update is two lines long, so I'm assuming I've got GRUB 2.

**Edit 2:** Turns out sda1 had been mounted when I ran the update-grub check. Ran it again and it went fine:

```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-13-generic
Found initrd image: /boot/initrd.img-2.6.38-13-generic
Found linux image: /boot/vmlinuz-2.6.32-37-generic
Found initrd image: /boot/initrd.img-2.6.32-37-generic
Found linux image: /boot/vmlinuz-2.6.32-33-generic
Found initrd image: /boot/initrd.img-2.6.32-33-generic
Found memtest86+ image: /boot/memtest86+.bin
done
```

But Windows 7 still isn't showing in GRUB when I boot.

---

### Post by oldfred on 2011-12-27
Perhaps a boot file missing, but to know what is where post this:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

---

### Post by Halfling Rogue on 2011-12-27
Thanks. Before running the boot script I also tried following the directions here: [http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338) to manually add Windows to the boot menu. It did, but when I try to run Windows I just get a black screen with no response. Ubuntu works, but the grub changes have lost the custom display drivers I had set up. >\

Here's results.txt:

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 2 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda1 has 
                       104853503 sectors, but according to the info from 
                       fdisk, it has 104854206 sectors.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   104,856,254   104,854,207   7 NTFS / exFAT / HPFS
/dev/sda2         104,856,255   209,712,509   104,856,255  83 Linux
/dev/sda3         209,712,510   213,905,474     4,192,965  82 Linux swap / Solaris
/dev/sda4         213,905,475   625,137,344   411,231,870   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        5648A5FE48A5DCCD                       ntfs       Windows7
/dev/sda2        0e8ef373-799f-4d11-8cca-3d8b4d4b6a94   ext4       Ubuntu
/dev/sda3        da7c6a47-e0f1-4e27-bb0a-71aed8405e56   swap       
/dev/sda4        1130D794514DED8C                       ntfs       storage

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro)
/dev/sda4        /media/storage           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


=========================== sda2/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 0e8ef373-799f-4d11-8cca-3d8b4d4b6a94
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1366x768
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 0e8ef373-799f-4d11-8cca-3d8b4d4b6a94
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/06_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

echo "Adding Ubuntu Lucid Lynx 10.04 LTS" >&2 
cat << EOF
menuentry "Ubuntu Lucid Lynx 10.04 LTS" {
    set root=(hd0,2)
        linux /vmlinuz root=/dev/sda2 ro quiet splash
        initrd /initrd.img
}
EOF

echo "Ubuntu Lucid Lynx 10.04 LTS (Recovery Mode)" >&2 
cat << EOF
menuentry "Ubuntu Lucid Lynx 10.04 LTS (Recovery Mode)" {
    set root=(hd0,2)
        linux /vmlinuz root=/dev/sda2 ro single
        initrd /initrd.img
}
EOF

echo "Windows 7" >&2 
cat << EOF
menuentry "Windows 7 (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 5648A5FE48A5DCCD
    chainloader +1
}
EOF
### END /etc/grub.d/06_custom ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.38-13-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 0e8ef373-799f-4d11-8cca-3d8b4d4b6a94
	linux	/boot/vmlinuz-2.6.38-13-generic root=UUID=0e8ef373-799f-4d11-8cca-3d8b4d4b6a94 ro   quiet splash
	initrd	/boot/initrd.img-2.6.38-13-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-13-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 0e8ef373-799f-4d11-8cca-3d8b4d4b6a94
	echo	'Loading Linux 2.6.38-13-generic ...'
	linux	/boot/vmlinuz-2.6.38-13-generic root=UUID=0e8ef373-799f-4d11-8cca-3d8b4d4b6a94 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-13-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-37-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 0e8ef373-799f-4d11-8cca-3d8b4d4b6a94
	linux	/boot/vmlinuz-2.6.32-37-generic root=UUID=0e8ef373-799f-4d11-8cca-3d8b4d4b6a94 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-37-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-37-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 0e8ef373-799f-4d11-8cca-3d8b4d4b6a94
	echo	'Loading Linux 2.6.32-37-generic ...'
	linux	/boot/vmlinuz-2.6.32-37-generic root=UUID=0e8ef373-799f-4d11-8cca-3d8b4d4b6a94 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-37-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-33-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 0e8ef373-799f-4d11-8cca-3d8b4d4b6a94
	linux	/boot/vmlinuz-2.6.32-33-generic root=UUID=0e8ef373-799f-4d11-8cca-3d8b4d4b6a94 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-33-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-33-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 0e8ef373-799f-4d11-8cca-3d8b4d4b6a94
	echo	'Loading Linux 2.6.32-33-generic ...'
	linux	/boot/vmlinuz-2.6.32-33-generic root=UUID=0e8ef373-799f-4d11-8cca-3d8b4d4b6a94 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-33-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 0e8ef373-799f-4d11-8cca-3d8b4d4b6a94
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 0e8ef373-799f-4d11-8cca-3d8b4d4b6a94
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sda2 :
UUID=0e8ef373-799f-4d11-8cca-3d8b4d4b6a94	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sda4 :
UUID=1130D794514DED8C	/media/storage	ntfs-3g	defaults,locale=en_US.utf8	0	0
#Entry for /dev/sda3 :
UUID=da7c6a47-e0f1-4e27-bb0a-71aed8405e56	none	swap	sw	0	0


--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  88.185882092 = 94.688869888   boot/grub/core.img                             1
  88.288688183 = 94.799257088   boot/grub/grub.cfg                             1
  88.262938976 = 94.771609088   boot/initrd.img-2.6.32-33-generic              1
  50.768870831 = 54.512659968   boot/initrd.img-2.6.32-37-generic              2
  50.741546154 = 54.483320320   boot/initrd.img-2.6.38-13-generic              2
  88.255145550 = 94.763240960   boot/vmlinuz-2.6.32-33-generic                 1
  88.276069164 = 94.785707520   boot/vmlinuz-2.6.32-37-generic                 1
  88.270282269 = 94.779493888   boot/vmlinuz-2.6.38-13-generic                 1
  50.768870831 = 54.512659968   initrd.img                                     2
  50.741546154 = 54.483320320   initrd.img.old                                 2
  88.276069164 = 94.785707520   vmlinuz                                        1
  88.270282269 = 94.779493888   vmlinuz.old                                    1

========= Devices which don't seem to have a corresponding hard drive: =========

sdb 


```

---

### Post by oldfred on 2011-12-27
You are missing the boot files in the bootable partition and the PBR or BS partition boot sector is not sized correctly. Did you shrink the Windows partition with gparted or the installer? Best to shrink Windows from inside Windows and use gparted to create partitions.

Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

You do not have a separate 100MB boot partition. You do have a copy of bootmgr in sda4, but do not show any BCD??

You need a Windows repair CD or USB to fix this. Did you make one before installing Ubuntu? Or do you have a full install DVD?

How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
# is comment do not copy or type comments
BootRec.exe /fixMBR   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r  #(have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector or see bootsect.exe commands
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by Halfling Rogue on 2011-12-28
No, I didn't shrink the Windows partition at all. I had the drive wiped and and built all the partitions from scratch using gparted, then did the installation. Windows was working fine until Ubuntu was installed and then it stopped.

I do have the Windows 7 full install on a USB. I'll try the boot repair, thanks.

---

### Post by Halfling Rogue on 2011-12-28
Apparently my version of Windows 7 doesn't come with a repair option; I could only get it to reinstall, and now grub seems to have been wiped and Windows is the default boot. There is no bootrec.exe on my install as far as I can tell, and I can't find where to download it on its own.


I'm torrenting a version of the repair disk that will hopefully fix the boot record, but not sure how to get grub back now.

---

### Post by grahammechanical on 2011-12-28
When Ubuntu changed from legacy Grub to Grub 2 it did not remove the original menu.lst file. It is possible to do a fresh install without formatting the / partition. In this case obsolete files will be over written but unwanted files may not be removed.

Is this what happened here? All I know is that I still had my Grub menu.lst file although the system was using Grub 2. I do not have it now as I have done a couple of fresh installs with a format of the / partition since then.

I can also recommend the drs305's work on our behalf to understand Grub 2. It is good stuff.

Regards.

---

### Post by oldfred on 2011-12-28
Fix boot loaders:

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)


Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

