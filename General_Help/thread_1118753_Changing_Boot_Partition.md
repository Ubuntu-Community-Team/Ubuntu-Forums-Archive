---
title: "Changing Boot Partition"
date: 2009-04-07
forum: General Help
---

### Post by mshumer on 2009-04-07
OK Guys and Gals, first thank all of you for an excellent forum. It has been extremely helpful. Now for my problem.
I have an Aspire One with 160GB hard drive. It came with Windoze XP which was deleted as soon as I powered up the machine. I have Ubuntu 8.04.1 installed and it works great. My problem is this: When I installed Ubuntu, I copied my /home partition from another machine so I have these partitions:
(Physical) sda1: 50GB, sda3: /home, (Logical) sda2: boot (contains sda5 which is root "/"

my root partition is too small (16 GB) and sda1 isn't being used at all. Don't know how it happened but it did. I want to make sda1 root and bootable. I have copied the contents of root to sda1 by booting to systemrescueCD, mouning sda6 as /source and sda1 as /target then using
cp -var /source/* /target/ to move files.

I have the contents of root on the sda1 and now want to boot from that partition. 
I booted from rescueCD and ran gparted. 
Set boot flag to sda1.   
ran grub
did "find /boot/grub/stage1    It showed (hd0,0) and (hd0,5) 
did "root (hd0,0)"
did "setup (hd0)"
and rebooted.
System didn't find boot partition and stopped.

I set everything back to (hd0,5) and system works again but I really want to move root system back to sda1. 
What now?

---

### Post by meierfra. on 2009-04-12
In order to get a clearer picture of your setup, I suggest to boot into  Ubuntu and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post,  highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by theozzlives on 2009-04-12
You might need to change the boot flag to sda1 in gparted.

---

### Post by mshumer on 2009-04-12
For theozzlives, I tried changing the boot flag to point at sda1 with gparted ran from bootCD but it didn't change anything. It still booted from sda5. 

Meierfra, Thanks for the script. Here's the results:

```
=================== Boot Info Summary: ===========================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.2
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.2
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x11a8ba38

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   104,904,449   104,904,387  83 Linux
/dev/sda2         271,771,605   312,576,704    40,805,100   5 Extended
/dev/sda5    *    271,771,668   309,267,314    37,495,647  83 Linux
/dev/sda6         309,267,378   312,576,704     3,309,327  82 Linux swap / Solaris
/dev/sda3         104,904,450   271,771,604   166,867,155  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="9d831074-b776-4c96-aa77-e9ca0e2415e9" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: UUID="40d3108e-1562-47f5-aa17-15dfef903d97" TYPE="ext3" 
/dev/sda5: UUID="7e7c2c05-940c-444b-9022-e6208e28737f" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="23f199e4-1d1a-4a9d-a878-ca72b2b637c4" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-22-generic/volatile type tmpfs (rw)
/dev/sda3 on /home type ext3 (rw,nosuid,nodev)
securityfs on /sys/kernel/security type securityfs (rw)


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
timeout		5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# root		(hd0,0)
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
# kopt=root=UUID=7e7c2c05-940c-444b-9022-e6208e28737f ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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
# howmany=3

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

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=7e7c2c05-940c-444b-9022-e6208e28737f ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=7e7c2c05-940c-444b-9022-e6208e28737f ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=9d831074-b776-4c96-aa77-e9ca0e2415e9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=fd58b6de-c458-401f-a246-001c3f0da321 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda3 /home ext3 nodev,nosuid 0 2

=================== sda1: Location of files loaded by Grub: ===================


  43.8GB: boot/grub/menu.lst
  43.8GB: boot/grub/stage2
  43.7GB: boot/initrd.img-2.6.24-19-generic
  43.7GB: boot/initrd.img-2.6.24-19-generic.bak
  43.7GB: boot/initrd.img-2.6.24-22-generic
  43.7GB: boot/initrd.img-2.6.24-22-generic.bak
  43.7GB: boot/initrd.img-2.6.24-23-generic
  43.7GB: boot/initrd.img-2.6.24-23-generic.bak
  43.7GB: boot/vmlinuz-2.6.24-19-generic
  43.7GB: boot/vmlinuz-2.6.24-22-generic
  43.7GB: boot/vmlinuz-2.6.24-23-generic
  43.7GB: initrd.img
  43.7GB: initrd.img.old
  43.7GB: vmlinuz
  43.7GB: vmlinuz.old

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
# kopt=root=UUID=7e7c2c05-940c-444b-9022-e6208e28737f ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

##title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
##root		(hd0,4)
##kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=7e7c2c05-940c-444b-9022-e6208e28737f ro quiet splash
##initrd		/boot/initrd.img-2.6.24-23-generic
##quiet

##title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
##root		(hd0,4)
##kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=7e7c2c05-940c-444b-9022-e6208e28737f ro single
##initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, kernel 2.6.24-22-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=7e7c2c05-940c-444b-9022-e6208e28737f ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=7e7c2c05-940c-444b-9022-e6208e28737f ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=7e7c2c05-940c-444b-9022-e6208e28737f ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=7e7c2c05-940c-444b-9022-e6208e28737f ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=7e7c2c05-940c-444b-9022-e6208e28737f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=fd58b6de-c458-401f-a246-001c3f0da321 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda3 /home ext3 nodev,nosuid 0 2

=================== sda5: Location of files loaded by Grub: ===================


 151.5GB: boot/grub/menu.lst
 152.1GB: boot/grub/stage2
 149.5GB: boot/initrd.img-2.6.24-19-generic
 149.4GB: boot/initrd.img-2.6.24-19-generic.bak
 146.4GB: boot/initrd.img-2.6.24-22-generic
 144.7GB: boot/initrd.img-2.6.24-22-generic.bak
 140.2GB: boot/initrd.img-2.6.24-23-generic
 150.3GB: boot/initrd.img-2.6.24-23-generic.bak
 149.5GB: boot/vmlinuz-2.6.24-19-generic
 149.6GB: boot/vmlinuz-2.6.24-22-generic
 140.3GB: boot/vmlinuz-2.6.24-23-generic
 140.2GB: initrd.img
 146.4GB: initrd.img.old
 140.3GB: vmlinuz
 149.6GB: vmlinuz.old
```

---

### Post by jocampo on 2009-04-12
HI

I think that you need to reinstall the MBR. Backup all your important data using the UBUNTU Live CD and do the following (of course, from Live CD)

1.>sudo mount /dev/sda1 /mnt
2.>sudo grub-install --root-directory=/mnt /dev/sda (you'll see about the script and the new installation)
3.Check if correct using cat/boot/grub/device.map
4.sudo umount /mnt

Now, sda1 should have your MBR and you should be able to boot from there. YOu probably will have to edit the /boot/grub/menu.lst and add your other entries if you're doing dual boot.

---

### Post by meierfra. on 2009-04-12
> kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=[COLOR="Red"]7e7c2c05-940c-444b-9022-e6208e28737f[/COLOR] ro quiet splash

the menu.lst on /dev/sda1 stills uses the UUID for /dev/sda5.
So you need to change that to "9d831074-b776-4c96-aa77-e9ca0e2415e9".


> ##title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
You are not using the 2.6.24-23 kernel for booting.  Is there something wrong with that kernel? If yes, you should use the  "2.6.24-22" kernel in menu.lst of /dev/sda1

Try those two changes, reinstall grub via "sudo grub, root (hd0,0), setup (hd0),quit" and see whether you are able to boot into your sda1 Ubuntu. If it does not work, report all error messages you got.

> my root partition is too small (16 GB) 
Since you have a home partition, 16GB should be  big enough. What does

```
df -h |grep sda5
```
show?

Did you consider using /dev/sda1 as a Data partition?

---

### Post by mshumer on 2009-04-13
Thanks to everyone for your assistance. I'm on the road and will try to update everything this weekend. I can see the incorrect UUID. Don't know why I didn't see that before. 

Yes, 2.6.24-23 kernel had problems with the Aspire One. Don't 
know why. It was just easier to boot back to the previous update.

I run BOINC software as well as writerscafe and there doesn't seem to be much room left on my boot partition. When I upgraded to the aspire one, my install left me sda1 as unused while it installed boot into a the logical partition sda5. Being too lazy to reinstall (yet), I'm wanting to move boot out from logical partition. 
I'll report on progress Sunday.
Thanks again to all for outstanding assistance. ;-)

---

