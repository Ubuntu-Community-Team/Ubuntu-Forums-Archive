---
title: "Error 12 with grub when trying booting windows."
date: 2009-02-08
forum: General Help
---

### Post by hattersluck on 2009-02-08
Last night I finally decided to go back and install Ubuntu after a hard drive failure. After install it didn't want to install GRUB so I went ahead and followed the instructions to install it via live cd.

I am able to boot happily in Linux with no problem but whenever I try to boot into Windows XP I get Error 12. I've tried running fixboot, I've re-written my MBR with FIXMBR and was able to boot into Windows XP again but no matter what I have been unable to use GRUB to boot into Windows.

I am currently running Ubuntu 8.10.

Would anyone be willing to assist me with this problem?

---

### Post by Monotoko on 2009-02-08
Invalid device requested....tell me, is it a clean install of XP?

---

### Post by caljohnsmith on 2009-02-08
In order to get a clearer picture of your setup, how about booting your Ubuntu Live CD (the Ubuntu install CD), download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to the Live CD desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by hattersluck on 2009-02-08
@Monotoko - No this is a 6 month old install of Windows.

@caljohnsmith - Done and done.

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on boot drive #2 in 
    partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3c473c46

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   877,341,779   877,341,717   7 HPFS/NTFS
/dev/sda2         877,341,780   976,768,064    99,426,285   f W95 Ext d (LBA)
/dev/sda5         877,341,843   972,607,229    95,265,387  83 Linux
/dev/sda6         972,607,293   976,768,064     4,160,772  82 Linux swap / Solaris


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x13171c4d

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *         16,065   398,283,479   398,267,415   f W95 Ext d (LBA)
/dev/sdb5              16,128   398,283,479   398,267,352   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="0A38C62138C60B9F" LABEL="Villain" TYPE="ntfs" 
/dev/sda5: UUID="3af310ea-c14f-4c76-8fa5-e14a63dc7284" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="7d97d650-bfc4-46e9-af1f-277b406f5b41" TYPE="swap" 
/dev/sdb5: UUID="1448E17448E154D0" LABEL="Games" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs" 

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

================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="XP" 

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP" 

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sda5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=3af310ea-c14f-4c76-8fa5-e14a63dc7284 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=3af310ea-c14f-4c76-8fa5-e14a63dc7284

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
uuid		3af310ea-c14f-4c76-8fa5-e14a63dc7284
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=3af310ea-c14f-4c76-8fa5-e14a63dc7284 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		3af310ea-c14f-4c76-8fa5-e14a63dc7284
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=3af310ea-c14f-4c76-8fa5-e14a63dc7284 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		3af310ea-c14f-4c76-8fa5-e14a63dc7284
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=3af310ea-c14f-4c76-8fa5-e14a63dc7284 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		3af310ea-c14f-4c76-8fa5-e14a63dc7284
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=3af310ea-c14f-4c76-8fa5-e14a63dc7284 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-3-rt
uuid		3af310ea-c14f-4c76-8fa5-e14a63dc7284
kernel		/boot/vmlinuz-2.6.27-3-rt root=UUID=3af310ea-c14f-4c76-8fa5-e14a63dc7284 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-3-rt
quiet

title		Ubuntu 8.10, kernel 2.6.27-3-rt (recovery mode)
uuid		3af310ea-c14f-4c76-8fa5-e14a63dc7284
kernel		/boot/vmlinuz-2.6.27-3-rt root=UUID=3af310ea-c14f-4c76-8fa5-e14a63dc7284 ro  single
initrd		/boot/initrd.img-2.6.27-3-rt

title		Ubuntu 8.10, memtest86+
uuid		3af310ea-c14f-4c76-8fa5-e14a63dc7284
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
root		(hd0,1)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb5
UUID=3af310ea-c14f-4c76-8fa5-e14a63dc7284 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb6
UUID=7d97d650-bfc4-46e9-af1f-277b406f5b41 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 455.0GB: boot/grub/menu.lst
 455.0GB: boot/grub/stage2
 455.0GB: boot/initrd.img-2.6.27-11-generic
 455.0GB: boot/initrd.img-2.6.27-3-rt
 455.0GB: boot/initrd.img-2.6.27-7-generic
 455.0GB: boot/vmlinuz-2.6.27-11-generic
 455.0GB: boot/vmlinuz-2.6.27-3-rt
 455.1GB: boot/vmlinuz-2.6.27-7-generic
 455.0GB: initrd.img
 455.0GB: initrd.img.old
 455.0GB: vmlinuz
 455.0GB: vmlinuz.old


```

---

### Post by caljohnsmith on 2009-02-08
According to the script results, you have Grub installed to the MBR (Master Boot Record) of both your HDDs, so from that standpoint it's ambiguous which drive you are booting on start up; booting either of your drives should give you a Grub menu. But since you got a Grub error 12 when booting Windows, that would mean you would have to be booting the Ubuntu/Windows sda drive on start up because of how the Windows entry is configured in your Grub's menu.lst. So to fix it, how about booting into your Ubuntu install, open a terminal, and pull up your menu.lst with:
```
gksudo gedit /boot/grub/menu.lst
```
Then replace your existing Windows entry with:
```
title Windows XP
root (hd0,0)
chainloader +1
```
Reboot, and let me know if you can boot Windows OK or if you run into problems.

---

### Post by hattersluck on 2009-02-08
Cal, you are a life saver that worked perfectly.

Thanks for all the help!

---

### Post by caljohnsmith on 2009-02-08
Glad that worked OK; cheers and enjoy Windows and Ubuntu. :)

---

