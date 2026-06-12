---
title: "how to generate new grub? the HD containing it colapse."
date: 2009-01-24
forum: General Help
---

### Post by kokorini on 2009-01-24
Hi! first of all, thank you very much!

I have 2 HD.

1) 20 Gb with:
-backups
-grub to select from the OpSystem.

2) 160 Gb SATA with:
-window$ xp
-ubuntu

the fact is that the little one colapse and stop working. So the computer boots from the SATA where are actually all the important things but was never the grub there.
so... how can I add it there?

some how I tried with "super grub editor" and now it show the grub menu but it says "file not found" on every option.

thank you very much again.

---

### Post by caljohnsmith on 2009-01-24
OK, how about when you get the Grub menu on start up, select the first Ubuntu entry, press "e" to edit it, select the line that says "root (hdX,Y)" where X and Y are numbers, press "e" to edit it, change it to "root (hd0,Y)", press return to save the change, then press "b" to boot. Based on the info you gave, I think that should be all it takes to boot Ubuntu. Note that the change is not permanent, so you'll need to modify your menu.lst to make it permanent.

So if it works, when you get into Ubuntu, just do:
```
gksudo gedit /boot/grub/menu.lst
```
And change the line that says "# groot=(hdX,Y)" to use the (hd0,Y) that worked to boot Ubuntu. Save, quit gedit, then run:
```
sudo update-grub
```
And you should be all set. Let me know how it goes or if you run into problems.

---

### Post by kokorini on 2009-01-24
Hi! thank you for your assistance.
I cant try to do what you say because now I see that there is no grub menu. it says something like "file not found"

then I boot again from this "super grub edit" cd...
and when I do "gksudo gedit /boot/grub/menu.lst" as you say it creates an empty file!

so... whats next?

thank you again!
Fgrant.

---

### Post by caljohnsmith on 2009-01-24
So what happens on start up? In your first post you said you used Super Grub to restore the Grub menu on start up, but now you don't get the Grub menu any more? In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your booting problem might be.

---

### Post by kokorini on 2009-01-24
ok... here it is:

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       swap

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.2
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disco /dev/sda: 160.0 GB, 160041885696 bytes
255 cabezas, 63 sectores/pista, 19457 cilindros, 312581808 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Identificador de disco: 0x8a52de7d

Partition  Boot        Start          End         Size  Id System

/dev/sda1    *            63  247,047,569  247,047,507   7 HPFS/NTFS
/dev/sda3        247,047,570  312,576,704   65,529,135   f W95 Ext'd (LBA)
/dev/sda5        309,845,718  312,576,704    2,730,987  82 Linux swap / Solaris
/dev/sda6        247,047,696  309,845,654   62,797,959  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="000000004499529B" LABEL="GINSENG" TYPE="ntfs" 
/dev/sda5: TYPE="swap" UUID="cb7c36d6-01d4-41d1-a23c-a5953fe0956a" 
/dev/sda6: UUID="1430c356-62ab-47c5-a36e-0cf2351bf0e3" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/cacao/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=cacao)
/dev/sda1 on /media/GINSENG type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)

================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sda6/boot/grub/menu.lst: ===========================


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb6
UUID=1430c356-62ab-47c5-a36e-0cf2351bf0e3 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=cb7c36d6-01d4-41d1-a23c-a5953fe0956a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda6: Location  of files loaded by Grub: ===================


 126.4GB: boot/grub/menu.lst
 128.7GB: boot/grub/stage2
 128.8GB: boot/initrd.img-2.6.24-19-generic
 128.8GB: boot/initrd.img-2.6.24-19-generic.bak
 128.8GB: boot/initrd.img-2.6.24-21-generic
 128.8GB: boot/initrd.img-2.6.24-21-generic.bak
 128.8GB: boot/initrd.img-2.6.24-22-generic
 128.8GB: boot/initrd.img-2.6.24-22-generic.bak
 137.7GB: boot/initrd.img-2.6.24-23-generic
 130.0GB: boot/initrd.img-2.6.24-23-generic.bak
 128.8GB: boot/vmlinuz-2.6.24-19-generic
 128.8GB: boot/vmlinuz-2.6.24-21-generic
 128.8GB: boot/vmlinuz-2.6.24-22-generic
 130.4GB: boot/vmlinuz-2.6.24-23-generic
 137.7GB: initrd.img
 128.8GB: initrd.img.old
 130.4GB: vmlinuz
 128.8GB: vmlinuz.old

=============================== StdErr Messages: ===============================

No errors were reported.



thank you again!

---

### Post by dcstar on 2009-01-24
> **kokorini said:**
> ok... here it is:

============================= Boot Info Summary: 
..........
=========================== sda6/boot/grub/menu.lst: ===========================

=================== sda6: Location  of files loaded by Grub:
......

There is one obvious problem, no menu.lst file on that hard disk.

---

### Post by caljohnsmith on 2009-01-24
It looks like something may have happened to your menu.lst. How about doing:
```
sudo mount /dev/sda6 /mnt
cat /mnt/boot/grub/menu.lst
```
If that does not show your menu.lst, how about doing:
```
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo chroot /mnt
rm /boot/grub/menu.lst
update-grub
```
And say yes at the prompt to create a new menu.lst. When it is done please post:
```
cat /boot/grub/menu.lst
exit
```
Then try rebooting, and let me know exactly what happens on start up.

---

### Post by kokorini on 2009-01-25
Hi again!

thanks! ubuntu start perfectly!!! so that very good! thanks.

But I need to make the "dark side", windows, to be in the menu too (I'm trying to leave it but for about a 15% of my tasks I need it). 

Actually, now it does not show any menu, it just start ubuntu.

here is the output you ask for:



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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

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
# kopt=root=UUID=1430c356-62ab-47c5-a36e-0cf2351bf0e3 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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

title        Ubuntu 8.04.2, kernel 2.6.24-23-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=1430c356-62ab-47c5-a36e-0cf2351bf0e3 ro quiet splash
initrd        /boot/initrd.img-2.6.24-23-generic
quiet

title        Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=1430c356-62ab-47c5-a36e-0cf2351bf0e3 ro single
initrd        /boot/initrd.img-2.6.24-23-generic

title        Ubuntu 8.04.2, kernel 2.6.24-22-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.24-22-generic root=UUID=1430c356-62ab-47c5-a36e-0cf2351bf0e3 ro quiet splash
initrd        /boot/initrd.img-2.6.24-22-generic
quiet

title        Ubuntu 8.04.2, kernel 2.6.24-22-generic (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.24-22-generic root=UUID=1430c356-62ab-47c5-a36e-0cf2351bf0e3 ro single
initrd        /boot/initrd.img-2.6.24-22-generic

title        Ubuntu 8.04.2, kernel 2.6.24-21-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.24-21-generic root=UUID=1430c356-62ab-47c5-a36e-0cf2351bf0e3 ro quiet splash
initrd        /boot/initrd.img-2.6.24-21-generic
quiet

title        Ubuntu 8.04.2, kernel 2.6.24-21-generic (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.24-21-generic root=UUID=1430c356-62ab-47c5-a36e-0cf2351bf0e3 ro single
initrd        /boot/initrd.img-2.6.24-21-generic

title        Ubuntu 8.04.2, kernel 2.6.24-19-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=1430c356-62ab-47c5-a36e-0cf2351bf0e3 ro quiet splash
initrd        /boot/initrd.img-2.6.24-19-generic
quiet

title        Ubuntu 8.04.2, kernel 2.6.24-19-generic (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=1430c356-62ab-47c5-a36e-0cf2351bf0e3 ro single
initrd        /boot/initrd.img-2.6.24-19-generic

title        Ubuntu 8.04.2, memtest86+
root        (hd0,5)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST



To put back windows in the menu, the caverns-man way I think is to make windows "repair himself" and if it remove the grub menu put it back with the SGD witch seems to be good for that.

is there a better way?

thank you very much!!

I hope to be as usefull as you are for me to the community soon!:D

---

### Post by caljohnsmith on 2009-01-25
OK, while you are in your Ubuntu install, how about first opening your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And at the bottom add:
```
title Windows XP
root (hd0,0)
chainloader +1
```
Then reboot, see if the Windows entry works, and if not let me know exactly what happens. We can work from there if necessary.

---

### Post by kokorini on 2009-01-26
Well... after adding what you say the menu wasn't show, so I used the GrubEd, a nice script I found, and tell him to show the menu and a few seconds more just in case it is a bad day and I need to use windows (more seconds because you have to be sure of that).

so now is everything on rails and working.
I have another issues but they a matter of another post so...

thank you very much again for all your help

F. Grant.

---

