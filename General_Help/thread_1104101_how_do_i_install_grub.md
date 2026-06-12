---
title: "how do i install grub?"
date: 2009-03-23
forum: General Help
---

### Post by Meow27 on 2009-03-23
hi, ive been having some trouble recently. i need to get grub2 on my external disk's MBR.

can someone tell me how to do this please?

---

### Post by cariboo on 2009-03-23
Are you sure you need grub2? it isn't really ready for prime time yet. You can instiall grub on your extrenal drive by typing in a terminal:

```
sudo grub-install (hd1)
```

grub starts counting drive and partitions from zero, so if you extrenal is your second drive it would be (hd1).

Jim

---

### Post by Meow27 on 2009-03-23
thanks for the reply!

ut now that you mention that, im gonna bring another question from a previous post

i have a data primary partition with a extended one with 4 partitions, 3 ext3 partitions and one swap.

i can make the 3 logical partitions bootable. right?

---

### Post by Meow27 on 2009-03-23
ok i tried it, it failed. it doesnt recognize the drive as "hd1"

---

### Post by Meow27 on 2009-03-24
bump

---

### Post by Meow27 on 2009-03-28
i dont mind installing gag either, 

i just need a partition manager that will work on my external disk

---

### Post by halavin on 2009-03-28
see your device.map file


and then do this: 

grub-install /dev/sda or what every your disk may be . 
make sure you dont do this on a wrong drive . 


Hope this helps

---

### Post by Meow27 on 2009-03-28
```
username@Nebula-Class:~$ sudo grub-install /dev/sdb
[sudo] password for username: 
/dev/sdb does not have any corresponding BIOS drive.

```

(and in case if ur wondering, it is the right harddisk, if i do sdc or something else, it'l tell me that there is nothing there)

---

### Post by meierfra. on 2009-03-29
> i just need a partition manager that will work on my external disk


Then grub (and not grub2) will be your best option. Could you describe what you are trying to accomplish?. Did you already install Ubuntu?

In order to get a clearer picture of your setup, I suggest to boot into  Ubuntu (or any kind of Linux OS or any kind  of Linux LiveCD)and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by Meow27 on 2009-03-29
why are you telling me to how to use the code function? i clearly have demonstrated that i use it in the above post >.>
anyhow here it is
```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.2
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2226eb33

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    25,607,609    25,607,547   7 HPFS/NTFS
/dev/sda2          25,607,610    87,104,429    61,496,820  83 Linux
/dev/sda3          87,104,430   156,296,384    69,191,955   f W95 Ext d (LBA)
/dev/sda5          87,104,493    91,313,459     4,208,967  82 Linux swap / Solaris
/dev/sda6          91,313,523   156,296,384    64,982,862   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6824b6d8

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   536,362,154   536,362,092   7 HPFS/NTFS
/dev/sdb2         536,362,155   625,137,344    88,775,190   5 Extended
/dev/sdb5         536,362,218   546,595,559    10,233,342   b W95 FAT32
/dev/sdb6         546,595,623   559,511,819    12,916,197  83 Linux
/dev/sdb7         559,511,883   563,704,784     4,192,902  82 Linux swap / Solaris
/dev/sdb8         563,704,785   625,137,344    61,432,560  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="52F419D3F419BA65" TYPE="ntfs" 
/dev/sda2: UUID="2b46f086-7b60-4f97-83e8-c05aee19ad67" TYPE="reiserfs" 
/dev/sda5: TYPE="swap" UUID="cb7661a2-f132-4a96-919a-efb993224319" 
/dev/sda6: UUID="01C9103411380E80" LABEL="Data" TYPE="ntfs" 
/dev/sdb1: UUID="C4E060ACE060A700" LABEL="Dan_Data" TYPE="ntfs" 
/dev/sdb5: LABEL="LIVE DISK" UUID="E8DD-28A5" TYPE="vfat" 
/dev/sdb6: UUID="b8227c3b-cc05-4688-92ad-d2d0014b04ee" TYPE="ext3" 
/dev/sdb7: TYPE="swap" UUID="cb759a21-6a93-4ee5-b10d-0bcb1487b349" 
/dev/sdb8: UUID="cdce904e-5869-4613-acec-106389b2044f" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sda2 on / type reiserfs (rw,relatime,notail)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw)
/dev/sda6 on /WIN_DATA type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
none on /proc/bus/usb type usbfs (rw,devgid=124,devmode=664)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/username/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=username)
/dev/sdb1 on /media/Dan_Data type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sdb5 on /media/LIVE DISK type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/sdb6 on /media/disk-1 type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sdb8 on /media/disk-2 type ext3 (rw,nosuid,nodev,uhelper=hal)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect




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
# kopt=root=UUID=2b46f086-7b60-4f97-83e8-c05aee19ad67 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=2b46f086-7b60-4f97-83e8-c05aee19ad67 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=2b46f086-7b60-4f97-83e8-c05aee19ad67 ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, kernel 2.6.24-22-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=2b46f086-7b60-4f97-83e8-c05aee19ad67 ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=2b46f086-7b60-4f97-83e8-c05aee19ad67 ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=2b46f086-7b60-4f97-83e8-c05aee19ad67 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=2b46f086-7b60-4f97-83e8-c05aee19ad67 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=2b46f086-7b60-4f97-83e8-c05aee19ad67 /               reiserfs notail,relatime 0       1
# /dev/sda6
UUID=01C9103411380E80 /WIN_DATA       ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=cb7661a2-f132-4a96-919a-efb993224319 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# For USB access with Virtualbox
none	/proc/bus/usb	usbfs	devgid=124,devmode=664	0	0

=================== sda2: Location of files loaded by Grub: ===================


  20.4GB: boot/grub/menu.lst
  15.7GB: boot/grub/stage2
  20.3GB: boot/initrd.img-2.6.24-19-generic
  20.3GB: boot/initrd.img-2.6.24-19-generic.bak
  20.4GB: boot/initrd.img-2.6.24-22-generic
  20.3GB: boot/initrd.img-2.6.24-22-generic.bak
  20.4GB: boot/initrd.img-2.6.24-23-generic
  20.4GB: boot/initrd.img-2.6.24-23-generic.bak
  20.3GB: boot/vmlinuz-2.6.24-19-generic
  20.3GB: boot/vmlinuz-2.6.24-22-generic
  20.4GB: boot/vmlinuz-2.6.24-23-generic
  20.4GB: initrd.img
  20.4GB: initrd.img.old
  20.4GB: vmlinuz
  20.3GB: vmlinuz.old
```

---

### Post by nebileix on 2009-03-29
> **meierfra. said:**
> Then grub (and not grub2) will be your best option. Could you describe what you are trying to accomplish?. Did you already install Ubuntu?

In order to get a clearer picture of your setup, I suggest to boot into  Ubuntu (or any kind of Linux OS or any kind  of Linux LiveCD)and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

Yeah... We dont know wat are you tryig to achieve here. Can u be more specific?

---

### Post by meierfra. on 2009-03-29
> why are you telling me to how to use the code function? i clearly have demonstrated that i use it in the above post 

Sorry. I'm just using a standard text whenever I request to run the boot info script.

I assume  /dev/sdb is your external hard drive. (or was the external drive not plugged when you run the boot info script?)


I'm not quite sure what you are trying to accomplish. You said that you want to install a boot loader to the MBR of the external drive.  Since there does not seem  to  be any operating systems on  the external drive, I assume you want to use is to load the OS's on the internal drive.

If this is the correct interpretation of your intentions:

```
sudo grub
```
and at the "grub>" prompt

```

device (hd0) /dev/sdb
device (hd1) /dev/sda
root (hd1,1)
setup (hd0)
quit
```

You will also have to edit menu.lst

```
gksudo gedit /boot/grub/menu.lst
```
Change 

# groot=(hd0,1)

to

# groot (hd1,1)

Change 


title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


to

title		Microsoft Windows XP Home Edition
root		(hd1,0)
map    (hd0) (hd1)
map    (hd1) (hd0)
savedefault
makeactive
chainloader	+1


Save and close the file. Back in the terminal:

```
sudo update-grub
```

Now when you boot from the external drive, you should get a grub menu which lets you boot into XP and Ubuntu.

Note: if you carry out these steps you won't be able to boot from the 
internal drive anymore.  If you want to remove Grub from the internal drive use

```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

Then booting from internal drive should boot you directly into XP.

If I misinterpreted your intention, let me know exactly what you are trying to accomplish, and we can work from there.

---

### Post by Meow27 on 2009-03-30
ok i havent tried what you just posted above, since you require an explanation

ive been struggling to get OSes to get working, ive been using software like Unetbootin, to burn some isos to some of those minor drives, it works, but the mbr doesn't appear to be touched, for this im thinking of using a boot manager specifically for my external disk so that i can multi-boot off of it in other computers.

my external drive in this case, is indeed sdb, and i dont need it on sdb to boot stuff on sda to clear that part up.

---

### Post by meierfra. on 2009-03-30
>  i havent tried what you just posted above,
Good. (I clearly misunderstood your intentions)

> a boot manager specifically for my external disk 

grub on the internal drive should be just as capable as grub on the internal drive. So I don't think putting a grub on the external drive will  improve the situation.

> my external drive in this case,
Boot from a external drive in a case can be a pain.
To test whether you are able to boot from the external drive, follow the direction from my previous post to install Grub to the MBR of the external drive.  

Then edit menu.lst as follows. Add

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic  (from external drive)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=2b46f086-7b60-4f97-83e8-c05aee19ad67 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

to the very end of menu.lst

This way you still will be able to boot into Ubuntu and XP as usual, and if you boot from the external drive, the newly added entry should boot you into Ubuntu. Then at least you will know that you are able to boot from the external drive.



> ive been using software like Unetbootin, 

I don't have much experience with Unetbootin. Are you following a specific tutorial?  I suggest to start a new thread and ask for help with Unetbootin. Provide as much information as possible. Describe exactly what you already tried.

---

### Post by Meow27 on 2009-03-30
arg, im telling you that im trying to use the hard disk like a liveUSB, its not gonna be always connected to my main computers >.>

hope that clears the rest of the problem>.>

also, where is the menu.lst ?

---

### Post by James_Lochhead on 2009-03-30
> **Meow27 said:**
> also, where is the menu.lst ?

/boot/grub/menu.lst

---

### Post by nebileix on 2009-04-08
> **Meow27 said:**
> arg, im telling you that im trying to use the hard disk like a liveUSB, its not gonna be always connected to my main computers >.>

hope that clears the rest of the problem>.>

also, where is the menu.lst ?

If ur mobo does boot from usb, have u tried System->Administration->Create a USB startup disk? U can save ur setting by allocating space on the disk.

---

### Post by Meow27 on 2009-04-10
> **nebileix said:**
> If ur mobo does boot from usb, have u tried System->Administration->Create a USB startup disk? U can save ur setting by allocating space on the disk.

that will only work if i have it as a primary partition, as a whole drive. additionally in this case it will have to be FAT in order to do that as well. 

ive already explained how my hdd looks like, 
two primary partions, one ntfs for data, another extended. 3 ext partitions with one swap should be inside, i reformatted one of them to fat to see if the above worked.... thanks for necroing the thread though :D

and the above is way too confusing for me atm. i think i need a detailed guide :/

---

### Post by nebileix on 2009-04-10
Alright. I think i know what you wanna do. Try this link [http://www.pendrivelinux.com/ubuntu-804-usb-hard-drive-install/]("http://www.pendrivelinux.com/ubuntu-804-usb-hard-drive-install/")
It'll install the OS to the external drive and install grub over there. You can actually skip the installation if you know how to setup grub into that drive. 

But first, you will need your mobo to be able to support for booting USB drive. Else you can forget the whole idea. Cuz I dun think your USB drivers will be loaded during grub menu, therefore, access to the USB external drive is not possible.

---

### Post by Meow27 on 2009-04-10
> **nebileix said:**
> Alright. I think i know what you wanna do. Try this link [http://www.pendrivelinux.com/ubuntu-804-usb-hard-drive-install/]("http://www.pendrivelinux.com/ubuntu-804-usb-hard-drive-install/")
It'll install the OS to the external drive and install grub over there. You can actually skip the installation if you know how to setup grub into that drive. 

But first, you will need your mobo to be able to support for booting USB drive. Else you can forget the whole idea. Cuz I dun think your USB drivers will be loaded during grub menu, therefore, access to the USB external drive is not possible.

please read the whole thread, it isn't that long. your suggestion has been suggested before, and again, im not gonna do that, cause the whole purpose of this is to install some bootloader onto my drive. not just one OS

---

### Post by nebileix on 2009-04-15
>  Originally Posted by nebileix  View Post
Alright. I think i know what you wanna do. Try this link [http://www.pendrivelinux.com/ubuntu-...drive-install/](http://www.pendrivelinux.com/ubuntu-...drive-install/)
It'll install the OS to the external drive and install grub over there. You can actually skip the installation if you know how to setup grub into that drive.

[COLOR="Blue"]But first, you will need your mobo to be able to support for booting USB drive[/COLOR]. Else you can forget the whole idea. Cuz I dun think your USB drivers will be loaded during grub menu, therefore, access to the USB external drive is not possible.
> **Meow27 said:**
> please read the whole thread, it isn't that long. your suggestion has been suggested before, and again, im not gonna do that, cause the whole purpose of this is to install some bootloader onto my drive. not just one OS

Make sure u have the grub boot directory in the external harddisk.
[http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html]("http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html")

---

