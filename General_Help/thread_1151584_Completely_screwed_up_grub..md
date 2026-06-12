---
title: "Completely screwed up grub."
date: 2009-05-07
forum: General Help
---

### Post by Zoowey on 2009-05-07
...and I mean COMPLETELY! I have tried so many things and all they do is restore grub, but I don't need it restored, I need it completly reinstalled. 

As far as I understand it I was messing around with Startup-Manager when I screwed up everything, I was lazy and just clicked "restore default bootloader options" BIG mistake. It seems to have used the grub backup file that was for Ubuntu 8.10, but I upgraded to 9.04 so that file won't boot up the system.

I've tried the "Sudo grub" "root (hd1,2)" "setup (hd0)" but that only restores it but doesn't "reset" my settings. I've also tried "sudo grub-install /dev/sdc3" and that just restored it as well. Also that one "sudo update-grub" command doesn't work either.

Please, any help would be greatly appreciated.

---

### Post by salvachn on 2009-05-07
Take a look here: 
[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

And I want to ask how you got the Ubuntu user number. I have a Linux user number from Linux Counter, but not an Ubuntu user number.

---

### Post by bacardiandwatermelon on 2009-05-07
Sorry if you have already seen this link...

[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by gamblor01 on 2009-05-07
> 
And I want to ask how you got the Ubuntu user number. I have a Linux user number from Linux Counter, but not an Ubuntu user number.


Google is your friend.  A simple search for "registered ubuntu user" took me here as the first link:

[http://ubuntucounter.geekosophical.net/](http://ubuntucounter.geekosophical.net/)

---

### Post by caljohnsmith on 2009-05-07
I think it would help to first get a clearer picture of your setup related to your booting problem, so how about downloading the **Boot Info Script** to your Ubuntu desktop (can be the Live CD):

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

John

---

### Post by Zoowey on 2009-05-07
> **caljohnsmith said:**
> I think it would help to first get a clearer picture of your setup related to your booting problem, so how about downloading the **Boot Info Script** to your Ubuntu desktop (can be the Live CD):

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

John

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on boot drive #3 in 
    partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     BootPart in the file 
                       /NST/nst_grub-8E6B0B693490CFAA1B62F34CAB3BC85F.mbr is 
                       trying to chain load sector #500970960 on boot drive #2
    Operating System:  Windows Vista
    Boot files/dirs:   /ubuntu/disks/boot/grub/menu.lst 
                       /ubuntu/winboot/menu.lst /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk

sdb1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sdb3 and 
                       looks at sector 828037048 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #3 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /etc/fstab

sdc1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sdc3 and 
                       looks at sector 590673400 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sdc. Stage2 looks on partition #3 for 
                       /boot/grub/menu.lst.
    Operating System:  Linux Mint 7 Gloria - Main 
                       Edition
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1e1d589a

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   976,771,071   976,769,024   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x24548d3f

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    25,173,854    25,173,792  82 Linux swap / Solaris
/dev/sdb2          25,173,855   500,970,959   475,797,105  83 Linux
/dev/sdb3    *    500,970,960   976,768,064   475,797,105  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0002d0a1

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63    25,173,854    25,173,792  82 Linux swap / Solaris
/dev/sdc2          25,173,855   500,970,959   475,797,105  83 Linux
/dev/sdc3    *    500,970,960   976,768,064   475,797,105  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="385869445869024C" TYPE="ntfs" 
/dev/sdb1: UUID="a9f146e4-4234-4e18-8327-0523bc53432c" TYPE="swap" 
/dev/sdb2: UUID="683a58b8-82fe-4426-b50c-fb4b22c0793d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb3: UUID="2432a04b-d275-4f4e-a59b-4219c6704cc3" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: UUID="d194aecd-52a6-4922-a8a5-f997064008ce" TYPE="swap" 
/dev/sdc2: UUID="8cd0c2d9-8cdc-47ac-8bb2-ff71e3533765" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc3: UUID="e497ee5f-bff3-4c74-9838-787de8778cab" SEC_TYPE="ext2" TYPE="ext3" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


==================== sda1/ubuntu/disks/boot/grub/menu.lst: ====================

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
# kopt=root=UUID=385869445869024C loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=385869445869024C loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=385869445869024C loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
chainloader	+1


======================== sda1/ubuntu/winboot/menu.lst: ========================

debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
	find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
	configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
	fallback 2
	find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
	configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
	fallback 3
	find --set-root --ignore-floppies /menu.lst
	configfile /menu.lst

title find /boot/grub/menu.lst
	fallback 4
	find --set-root --ignore-floppies /boot/grub/menu.lst
	configfile /boot/grub/menu.lst

title find /grub/menu.lst
	fallback 5
	find --set-root --ignore-floppies /grub/menu.lst
	configfile /grub/menu.lst

title commandline
	commandline

title reboot
	reboot

title halt
	halt

================================== sda1Wubi: ==================================

Operating System: "Ubuntu 8.10"

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  21.0GB: ubuntu/disks/boot/grub/menu.lst
 294.1GB: ubuntu/disks/boot/initrd.img-2.6.27-7-generic
 335.2GB: ubuntu/disks/boot/vmlinuz-2.6.27-7-generic

=============================== sdb3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb3
UUID=2432a04b-d275-4f4e-a59b-4219c6704cc3 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb2
UUID=683a58b8-82fe-4426-b50c-fb4b22c0793d /home           ext3    relatime        0       2
# /dev/sdb1
UUID=a9f146e4-4234-4e18-8327-0523bc53432c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb3: Location of files loaded by Grub: ===================


 423.9GB: boot/initrd.img-2.6.27-11-generic
 423.9GB: boot/vmlinuz-2.6.27-11-generic
 423.9GB: initrd.img
 423.9GB: vmlinuz

=========================== sdc3/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=e497ee5f-bff3-4c74-9838-787de8778cab ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e497ee5f-bff3-4c74-9838-787de8778cab

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

title		Ubuntu 9.04, kernel 2.6.28-12-server
uuid		e497ee5f-bff3-4c74-9838-787de8778cab
kernel		/boot/vmlinuz-2.6.28-12-server root=UUID=e497ee5f-bff3-4c74-9838-787de8778cab ro quiet splash 
initrd		/boot/initrd.img-2.6.28-12-server

title		Ubuntu 9.04, kernel 2.6.28-12-server (recovery mode)
uuid		e497ee5f-bff3-4c74-9838-787de8778cab
kernel		/boot/vmlinuz-2.6.28-12-server root=UUID=e497ee5f-bff3-4c74-9838-787de8778cab ro  single
initrd		/boot/initrd.img-2.6.28-12-server

title		Ubuntu 9.04, memtest86+
uuid		e497ee5f-bff3-4c74-9838-787de8778cab
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdc3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc3
UUID=e497ee5f-bff3-4c74-9838-787de8778cab /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc2
UUID=8cd0c2d9-8cdc-47ac-8bb2-ff71e3533765 /home           ext3    relatime        0       2
# /dev/sdc1
UUID=d194aecd-52a6-4922-a8a5-f997064008ce none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdc3: Location of files loaded by Grub: ===================


 302.5GB: boot/grub/menu.lst
 302.4GB: boot/grub/stage2
 302.4GB: boot/initrd.img-2.6.28-12-server
 302.4GB: boot/vmlinuz-2.6.28-12-server
 302.4GB: initrd.img
 302.4GB: vmlinuz
```

---

### Post by caljohnsmith on 2009-05-07
First off, it looks like you should be able to boot your 500 GB sdc drive and boot into Linux Mint OK. Is the issue with your Ubuntu install on sdb3? If it is, can you set your BIOS to boot the sdb drive first on start up? If so, how about doing the following from your Live CD:
```
sudo mount /dev/sdb3 /mnt
sudo grub-install --root-directory=/mnt --recheck /dev/sdb
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo chroot /mnt /bin/bash
update-grub  [COLOR="Blue"][note: say "y" when it asks if you want to create a new menu.lst][/COLOR]
cat /boot/grub/menu.lst
exit
```
And please post the output of all the above commands. If you don't get any errors, go ahead and reboot, set your sdb drive to boot first in your BIOS, and let me know how far you get. We can work from there.

John

---

### Post by Zoowey on 2009-05-07
I don't have Linux Mint installed. It's just a linux mint package I installed so I could use mintMenu and it changed some of Ubuntu's naming property's. This is 100% Ubuntu. and it's actually on sdc3. I think I have Ubuntu 8.10 on sdb but that is a left over instillation with no importance.

---

### Post by Zoowey on 2009-05-07
Ok, I seem to have repaired grub. I just tried "sudo grub-install /dev/sdc3" and it took a while but whatever it did, it fixed grub! I can now boot into Ubuntu again. 

It seems that last time I tried running "grub-install" I told it the root partition was sdc2 and the reason I did that is because grub numbers the devices from 0 but the BIOS numbers them from 1, so I got confused and thought that if I put sdc2 it will be sdc3 because of it starting from 0 which was not the case.

Thank you for all your help and I'm sorry to have waisted your time.

P.S. Grub's great but whoever came up with the idea to start mapping devices from 0 instead of 1 should have thought about it more.

---

### Post by theozzlives on 2009-05-07
> **Zoowey said:**
> Ok, I seem to have repaired grub. I just tried "sudo grub-install /dev/sdc3" and it took a while but whatever it did, it fixed grub! I can now boot into Ubuntu again. 

It seems that last time I tried running "grub-install" I told it the root partition was sdc2 and the reason I did that is because grub numbers the devices from 0 but the BIOS numbers them from 1, so I got confused and thought that if I put sdc2 it will be sdc3 because of it starting from 0 which was not the case.

Thank you for all your help and I'm sorry to have waisted your time.

P.S. Grub's great but whoever came up with the idea to start mapping devices from 0 instead of 1 should have thought about it more.

Hexadecimal begins at 0... 0-9, & A-F

---

### Post by gamblor01 on 2009-05-08
> 
P.S. Grub's great but whoever came up with the idea to start mapping devices from 0 instead of 1 should have thought about it more.


Most numbering schemas related to computer hardware begin with 0 -- it's just something that you have to get used to.  I know it seems weird at first but really it's because many times you are specifying memory addresses, and the system uses the base memory address plus an offset.

This happens quite regularly in programming.  Suppose you have an array (which is just a sequence of values that are stored contiguously in memory).  The variable holding your array is really just the memory address of the first element.  So if you want to get the first element out of the array then you need to tell the system to go that memory address and then go 0 bytes past it to get the first element.  It's already at the first element so certainly you don't need to add anything to that address in order to get it.  So the first element is at offset 0, the next one is at offset 1, and so on.

---

### Post by Zoowey on 2009-05-08
> **gamblor01 said:**
> Most numbering schemas related to computer hardware begin with 0 -- it's just something that you have to get used to.  I know it seems weird at first but really it's because many times you are specifying memory addresses, and the system uses the base memory address plus an offset.

This happens quite regularly in programming.  Suppose you have an array (which is just a sequence of values that are stored contiguously in memory).  The variable holding your array is really just the memory address of the first element.  So if you want to get the first element out of the array then you need to tell the system to go that memory address and then go 0 bytes past it to get the first element.  It's already at the first element so certainly you don't need to add anything to that address in order to get it.  So the first element is at offset 0, the next one is at offset 1, and so on.

Yes, I understand that it makes sense to use 0's within Computer Science and such but in the general world 0 just isn't used. As far as I understand it Grub2 will start mapping devices from 1. The programmer who makes grub may use 0 in his programming language or whatever but it's just not needed to add that programming idea in a general application used mostly by regular users.

---

### Post by gamblor01 on 2009-05-08
> 
The programmer who makes grub may use 0 in his programming language or whatever but it's just not needed to add that programming idea in a general application used mostly by regular users.

Agreed -- but programmers are lazy, you see.  That's why commands in Linux are abbreviated such as "rm" or "mv".  Who would want to type out the entire word "remove" or "move"?  That's just crazy talk.  ;)

---

