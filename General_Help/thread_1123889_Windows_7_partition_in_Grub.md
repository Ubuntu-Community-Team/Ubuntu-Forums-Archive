---
title: "Windows 7 partition in Grub"
date: 2009-04-12
forum: General Help
---

### Post by adam35413 on 2009-04-12
I just installed 9.04 beta on my laptop and everything worked great.  I can see my Windows 7 drive in Ubuntu and I can mount it.  However, Grub does not see the partition when I boot up.  Is there a setting I need to change to make sure it is seen?

---

### Post by meierfra. on 2009-04-12
In order to get a clearer picture of your setup, I suggest to boot into  Ubuntu and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post,  highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might

---

### Post by adam35413 on 2009-04-12
Here is the information you requested: 

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu jaunty (development 
                       branch)
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /BOOT.INI /bootmgr /BOOTMGR /ntldr /NTLDR 
                       /NTDETECT.COM /ntdetect.com

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x68000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       192,779       192,717  de Dell Utility
/dev/sda2    *        192,780   205,599,869   205,407,090  83 Linux
/dev/sda3         205,608,960   347,035,647   141,426,688   7 HPFS/NTFS
/dev/sda4         347,036,191   625,139,711   278,103,521   f W95 Ext d (LBA)
/dev/sda5         619,898,880   625,139,711     5,240,832  dd 
/dev/sda6         347,036,193   355,036,499     8,000,307  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D8-060E" TYPE="vfat" 
/dev/sda2: UUID="08dfff06-7a24-4a34-bf50-2ddf58bd8953" TYPE="ext3" 
/dev/sda3: UUID="7A48BC4348BBFFC5" TYPE="ntfs" 
/dev/sda5: LABEL="MEDIADIRECT" UUID="28CF-3223" TYPE="vfat" 
/dev/sda6: UUID="f997043f-9dcb-4aba-826d-4a896c35c261" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/adam/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=adam)


=========================== sda2/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=08dfff06-7a24-4a34-bf50-2ddf58bd8953 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=08dfff06-7a24-4a34-bf50-2ddf58bd8953

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

title		Ubuntu jaunty (development branch), kernel 2.6.28-11-generic
uuid		08dfff06-7a24-4a34-bf50-2ddf58bd8953
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=08dfff06-7a24-4a34-bf50-2ddf58bd8953 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu jaunty (development branch), kernel 2.6.28-11-generic (recovery mode)
uuid		08dfff06-7a24-4a34-bf50-2ddf58bd8953
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=08dfff06-7a24-4a34-bf50-2ddf58bd8953 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu jaunty (development branch), memtest86+
uuid		08dfff06-7a24-4a34-bf50-2ddf58bd8953
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda5
title		Microsoft Windows XP Embedded
rootnoverify	(hd0,4)
savedefault
makeactive
chainloader	+1


=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=08dfff06-7a24-4a34-bf50-2ddf58bd8953 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=f997043f-9dcb-4aba-826d-4a896c35c261 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


  53.0GB: boot/grub/menu.lst
  53.0GB: boot/grub/stage2
  53.0GB: boot/initrd.img-2.6.28-11-generic
  52.9GB: boot/vmlinuz-2.6.28-11-generic
  53.0GB: initrd.img
  52.9GB: vmlinuz

================================ sda5/boot.ini: ================================

[boot loader]

timeout=0

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Embedded" /fastdetect /KERNEL=NTOSBOOT.EXE /maxmem=1024


================================ sda5/BOOT.INI: ================================

[boot loader]

timeout=0

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Embedded" /fastdetect /KERNEL=NTOSBOOT.EXE /maxmem=1024

```

Thoughts?

---

### Post by meierfra. on 2009-04-12
Strange situation: most of the boot files are on  the  logical partition/dev/sda5:

> sda5: 
    Boot files/dirs:   /boot.ini /BOOT.INI /bootmgr /BOOTMGR /ntldr /NTLDR 
                       /NTDETECT.COM /ntdetect.com


Windows never puts the boot  files on a logical partition. Did you move the boot files? Or did you move the whole partition?
Also the folder "BCD" is missing.

Anyway, try this:

Boot into Ubuntu, open a terminal  and open menu.lst via

```
gksudo gedit /boot/grub/menu.lst
```

add this to the very end of the file:

title		Windows 7
rootnoverify	(hd0,2)
chainloader	+1

Save the file.

Also set the boot flag to the Windows 7 partition:

```
sudo sfdisk -A3 /dev/sda
```
Save the file.


Next boot from your Windows 7 DVD.  Choose "Repair computer".  If the  DVD  offers you to fix a start up problem say yes. Otherwise, choose "StartUp Repair" at the new screen.

You might have to run "StartUp Repair" a few times, until it does not find any more errors.   

Then boot from the hard drive and choose "Window 7" at the grub menu.  If this does not let you boot into Win 7, come back here and report any error messages you got.

---

### Post by adam35413 on 2009-04-12
That solved it.  I went into the Windows 7 DVD and selected repair first.  Windows ran and then restarted.  At this point, Grub found Windows 7.  When I tried to boot into 7, it said BOOTMGR missing.  I booted back into the Windows 7 DVD and ran repair again.  This time, I had to go all the way to Startup Repair, and the repair ran and restarted.  This time, I was able to boot into Windows just fine.  

Thanks a lot!

---

### Post by meierfra. on 2009-04-12
```
This time, I was able to boot into Windows just fine.
```

Great. Do you have XP installed on /dev/sda5 and, if yes, are you able to boot into XP?

---

