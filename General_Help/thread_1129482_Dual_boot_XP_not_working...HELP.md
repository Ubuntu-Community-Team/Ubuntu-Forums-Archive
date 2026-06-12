---
title: "Dual boot XP not working...HELP"
date: 2009-04-18
forum: General Help
---

### Post by ectoplasm on 2009-04-18
So I've been dual booting Ubuntu and XP for about 6 months now, and everything was fine- I wanted to try Linux Mint so I got rid of intrepid and tried to dual boot Mint by using the partition editor...easy right. So for some reason the editor didn't recognize both of my hard drives, only one, where windows is stored ( my main idea was to have xp on one drive and linux on the other). The drive was partitioned as a FAT32, so I cut it up and allocated about 15 gigs for mint. I installed the distro on the empty space and it runs great, only thing is that XP won't boot now. When I boot it this come up: 

error 21: selected disk does not exist.

I've read different things about boot order and such but nothing has worked... Any help would be greatly appreciated!

---

### Post by Tim Sharitt on 2009-04-18
Can you post the output of sudo fdisk -l and the contents /boot/grub/menu.lst from Linux?

Note: Please enclose these with the code tags.

---

### Post by perrti-y02 on 2009-04-18
try typing 

sudo update-grub

into the terminal. This might work in that it may find the XP partition again.

---

### Post by ectoplasm on 2009-04-18
Ok here it is, if you need anything else I'll be glad to post:

_sudo fdisk -l_

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfe1efe1e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2014    16177423+   c  W95 FAT32 (LBA)
/dev/sda2            2015       12160    81497745    f  W95 Ext'd (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda5            3662       12160    68266768+   7  HPFS/NTFS
/dev/sda6            2015        3586    12627027   83  Linux
/dev/sda7            3587        3661      602406   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 8039 MB, 8039300608 bytes
255 heads, 63 sectors/track, 977 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc935c935

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         976     7839698    b  W95 FAT32


_sudo gedit /boot/grub/menu.lst_


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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## Graphical boot menu location
gfxmenu=/boot/gfxmenu/default.message

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=/dev/sda6 ro

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
##      altoptions=(single-user) single
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

title		Microsoft Windows XP Professional
root		(hd0,6)
map             (hd0,6)(hd0,0)
map             (hd0,0)(hd0,6)
makeactive
chainloader	+1

title		Linux Mint 6, kernel 2.6.27-7-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/sda6 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Linux Mint 6, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/sda6 ro single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Linux Mint 6, kernel Last successful boot
root		(hd0,5)
kernel		/boot/last-good-boot/vmlinuz root=/dev/sda6 ro quiet splash  last-good-boot
quiet

title		Linux Mint 6, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda6
title		Microsoft Windows XP Professional
root		(hd1,0)
map             (hd1,0)(hd0,0)
map             (hd0,0)(hd1,0)
makeactive
chainloader	+1


PS- I started researching different solutions which is why the grub looks so whack right now- I was testing out. thanks!

---

### Post by Tim Sharitt on 2009-04-18
Try changing

```
title Microsoft Windows XP Professional
root (hd1,0)
map (hd1,0)(hd0,0)
map (hd0,0)(hd1,0)
makeactive
chainloader +1
```
(the last entry in menu.lst)

to

```
title Microsoft Windows XP Professional
root (hd0,4)
makeactive
chainloader +1
```

---

### Post by ectoplasm on 2009-04-18
gave me a new error,

error 12: invalid device requested

---

### Post by meierfra. on 2009-04-18
Try 

title Microsoft Windows XP Professional
root (hd0,0)
chainloader +1

[B]If this does not work:
[/B]

In order to get a clearer picture of your setup, I suggest to boot into  Ubuntu and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post,  highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by ectoplasm on 2009-04-19
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /BOOT.INI /ntldr /NTLDR /NTDETECT.COM 
                       /ntdetect.com

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 6 Felicia
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfe1efe1e

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    32,354,909    32,354,847   c W95 FAT32 (LBA)
/dev/sda2          32,354,910   195,350,399   162,995,490   f W95 Ext d (LBA)
/dev/sda5          58,816,863   195,350,399   136,533,537   7 HPFS/NTFS
/dev/sda6          32,355,036    57,609,089    25,254,054  83 Linux
/dev/sda7          57,609,153    58,813,964     1,204,812  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8039 MB, 8039300608 bytes
255 heads, 63 sectors/track, 977 cylinders, total 15701759 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc935c935

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  44    15,679,439    15,679,396   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: LABEL="PRESARIO_RP" UUID="3679-0C85" TYPE="vfat" 
/dev/sda5: UUID="82689E21689E144F" TYPE="ntfs" 
/dev/sda6: UUID="9a06d8f0-e14c-4d02-b8b6-c78ef3280e33" TYPE="ext3" 
/dev/sda7: UUID="926b2dc5-3498-47ea-8373-9d424c7e4a77" TYPE="swap" 
/dev/sdb1: LABEL="My GS Drive" UUID="7026-9402" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/bryan/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=bryan)
/dev/sdb1 on /media/My GS Drive type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=15

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


================================ sda1/BOOT.INI: ================================

[boot loader]

timeout=15

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sda6/boot/grub/menu.lst: ===========================

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## Graphical boot menu location
gfxmenu=/boot/gfxmenu/default.message

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=/dev/sda6 ro

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
##      altoptions=(single-user) single
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

title		Microsoft Windows XP Professional
root		(hd0,1)
map             (hd0,1)(hd0,0)
map             (hd0,0)(hd0,1)
makeactive
chainloader	+1

title		Linux Mint 6, kernel 2.6.27-7-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/sda6 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Linux Mint 6, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/sda6 ro single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Linux Mint 6, kernel Last successful boot
root		(hd0,5)
kernel		/boot/last-good-boot/vmlinuz root=/dev/sda6 ro quiet splash  last-good-boot
quiet

title		Linux Mint 6, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1

title Microsoft Windows XP Professional
root (hd0,0)
chainloader +1


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=9a06d8f0-e14c-4d02-b8b6-c78ef3280e33 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=926b2dc5-3498-47ea-8373-9d424c7e4a77 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


  19.4GB: boot/grub/menu.lst
  19.4GB: boot/grub/stage2
  19.2GB: boot/initrd.img-2.6.27-7-generic
  19.2GB: boot/vmlinuz-2.6.27-7-generic
  19.2GB: initrd.img
  19.2GB: vmlinuz
```

---

### Post by meierfra. on 2009-04-19
What  error messages did you  get, when  tried booting with

title Microsoft Windows XP Professional
root (hd0,0)
chainloader +1

 Was it Error 21 or something different?

Everything seems to be  configured correctly.   Maybe this is on of the rare case,  where grub is not able to chainload XP, and  you have to add Ubuntu to the XP boot loader.

I can show you how to do that, but  first let me know what error message you got.

---

### Post by ectoplasm on 2009-04-19
when I enter your config it gives me NTLDR is missing

---

### Post by meierfra. on 2009-04-19
> when I enter your config it gives me NTLDR is missing
Strange.


> Disk /dev/sdb: 8039 MB, 8039300608 bytes
255 heads, 63 sectors/track, 977 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc935c935

Device Boot Start End Blocks Id System
/dev/sdb1 1 976 7839698 b W95 FAT32

Is this a flash drive?  Are your bios set  to boot from the flash drive?  If yes, I suggest to set you bios to boot from 100 GB drive. If this does not make a difference, see what happens if you unplug the 8GB drive.

---

### Post by ectoplasm on 2009-04-20
No dice with the removable of the flash drive...

do you think it has anything to do with editing a FAT32 partition to put linux in? I just feel like windows really hated me putting ubuntu on the same hard drive...I think we might have to say goodbye to grub though. If you're still up on that offer to show me how to switch boot loaders I'd really appreciate it. :)

---

### Post by meierfra. on 2009-04-20
```
do you think it has anything to do with editing a FAT32 partition to put linux in?
```
I don't know. The "ntldr missing" error really confuses me 

> If you're still up on that offer to show me how to switch boot loaders I'd really appreciate it.

Sure. 

**Step 1** Install Grub to the boot sector of the Linux Mint Partition:


```
sudo grub
```

and at the grub prompt:

```
root (hd0,5)
setup (hd0,5)
quit

```
[B]
Step 2[/B] Copy the Linux Mint boot sector to a file on your Windows partition:

```
sudo mount /dev/sda1 /mnt
sudo dd if=/dev/sda6 of=/mnt/mint.bin count=1
```
(be very careful with the "dd" command. If it runs for more than just a few seconds, press "Ctr+C" to stop the process.)

**Step 3 **Edit boot.ini:

```
sudo nano /mnt/boot.ini
```
(Do not use "gedit" in place of "nano": gedit  does not handle "dos" files very well)

Add this to the end of the file (start a new line, but to not leave a blank line):

C:\mint.bin="Linux Mint"

Follow the instructions at the bottom of the terminal to save the file.

**Step 4** Install a Windows Type MBR

```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

Reboot. You should get the Windows boot menu from which  you can boot XP and Linux Mint.

If you still aren't able to boot into XP, run "fixmbr" from the repair console of your Windows CD.

---

### Post by ectoplasm on 2009-04-20
You've been a saint my friend! Thank you for all your help and patience, I really appreciate it.

---

### Post by meierfra. on 2009-04-20
Glad it worked out. Just curious, did you have to  run "fixmbr" from the Windows CD?

---

