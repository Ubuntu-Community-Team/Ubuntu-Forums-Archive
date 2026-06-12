---
title: "Need some help with 8.10/XP Dual boot."
date: 2009-02-01
forum: General Help
---

### Post by Noxfaratos on 2009-02-01
I've searched everywhere, tried everything, and I still haven't been able to make a Dual boot with XP/8.10. I've edited the "gksudo gedit /boot/grub/menu.lst"
file and I still can't get it to work. Here's what it says.
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
# kopt=root=UUID=cc1dbb5a-2c5b-4d99-b6a3-6d3b5fcfa637 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=cc1dbb5a-2c5b-4d99-b6a3-6d3b5fcfa637

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
uuid		cc1dbb5a-2c5b-4d99-b6a3-6d3b5fcfa637
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=cc1dbb5a-2c5b-4d99-b6a3-6d3b5fcfa637 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		cc1dbb5a-2c5b-4d99-b6a3-6d3b5fcfa637
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=cc1dbb5a-2c5b-4d99-b6a3-6d3b5fcfa637 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		cc1dbb5a-2c5b-4d99-b6a3-6d3b5fcfa637
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=cc1dbb5a-2c5b-4d99-b6a3-6d3b5fcfa637 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		cc1dbb5a-2c5b-4d99-b6a3-6d3b5fcfa637
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=cc1dbb5a-2c5b-4d99-b6a3-6d3b5fcfa637 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		cc1dbb5a-2c5b-4d99-b6a3-6d3b5fcfa637
kernel		/boot/memtest86+.bin
quiet

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Windows XP Home Edition
root        (hd0,1)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1




### END DEBIAN AUTOMAGIC KERNELS LIST
```

Can anyone tell me what to do?

---

### Post by TreeFinger on 2009-02-01
what do you mean by 'haven't been able to boot' ?

---

### Post by Noxfaratos on 2009-02-01
It loads the Grub Dualboot menu, and I can't get Windows to work properly.

---

### Post by Martin Witte on 2009-02-01
> **Noxfaratos said:**
> I've searched everywhere, tried everything, and I still haven't been able to make a Dual boot with XP/8.10. I've edited the "gksudo gedit /boot/grub/menu.lst"
file and I still can't get it to work. Here's what it says.
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
# kopt=root=UUID=cc1dbb5a-2c5b-4d99-b6a3-6d3b5fcfa637 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=cc1dbb5a-2c5b-4d99-b6a3-6d3b5fcfa637

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
uuid		cc1dbb5a-2c5b-4d99-b6a3-6d3b5fcfa637
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=cc1dbb5a-2c5b-4d99-b6a3-6d3b5fcfa637 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		cc1dbb5a-2c5b-4d99-b6a3-6d3b5fcfa637
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=cc1dbb5a-2c5b-4d99-b6a3-6d3b5fcfa637 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		cc1dbb5a-2c5b-4d99-b6a3-6d3b5fcfa637
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=cc1dbb5a-2c5b-4d99-b6a3-6d3b5fcfa637 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		cc1dbb5a-2c5b-4d99-b6a3-6d3b5fcfa637
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=cc1dbb5a-2c5b-4d99-b6a3-6d3b5fcfa637 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		cc1dbb5a-2c5b-4d99-b6a3-6d3b5fcfa637
kernel		/boot/memtest86+.bin
quiet

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Windows XP Home Edition
root        (hd0,1)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1




### END DEBIAN AUTOMAGIC KERNELS LIST
```

Can anyone tell me what to do?

The Ubuntu blocks seem to have a wrong 'root' entry, I have:
```
## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=8607b5a5-3046-4967-909b-02106264aff7 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=8607b5a5-3046-4967-909b-02106264aff7 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


```

The root entry specifies which partition to use on which installed disk, start counting with zero. You can find your partitions with 'sudo parted' then use 'print' at the 'parted' prompt:
```
martin@toshibap200:~$ sudo parted
[sudo] password for martin: 
GNU Parted 1.8.9
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print                                                            
Model: ATA Hitachi HTS54161 (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  1574MB  1573MB  primary   ntfs              
 2      1574MB  61.6GB  60.0GB  primary   ntfs         boot 
 3      61.6GB  120GB   58.4GB  extended                    
 5      61.6GB  65.7GB  4096MB  logical   linux-swap        
 6      65.7GB  120GB   54.3GB  logical   ext3              

(parted) 


```
In my situation this tells me windows vista is on partition 2, and ubuntu on partition 6. If you need more help can you sHow us the output of print on the parted prompt?

---

### Post by Noxfaratos on 2009-02-01
```
huft@Computer:~$ sudo parted
[sudo] password for huft: 
GNU Parted 1.8.9
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print
Model: ATA ST3160021A (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system  Flags
 1      32.3kB  159GB  159GB   primary   ext3         boot 
 2      159GB   160GB  1349MB  extended                    
 5      159GB   160GB  1349MB  logical   linux-swap        

(parted)
```


I might have accidentally deleted Windows.

If anyone can talk to me Via AIM, mine is christianhuft.

---

### Post by caljohnsmith on 2009-02-01
> **Martin Witte said:**
> The Ubuntu blocks seem to have a wrong 'root' entry...
Just an FYI, Intrepid comes with an updated version of Grub that can now use UUIDs to select partitions, so you don't have to use the older "root (hdX,Y)" notation; thus the "uuid ......" line replaces the root line. Either works. :)

**Noxfaratos**, how about also posting:
```
sudo fdisk -lu
```
But unfortunately, yes, it does look like you might have deleted Windows if Windows was on the same drive as Ubuntu.

---

### Post by Martin Witte on 2009-02-02
> **caljohnsmith said:**
> Just an FYI, Intrepid comes with an updated version of Grub that can now use UUIDs to select partitions, so you don't have to use the older "root (hdX,Y)" notation; thus the "uuid ......" line replaces the root line. Either works. :)
Cool, didn't know this. My system started as a 7.04, and updated since then to all inbetween versions, that explains then my menu.lst

---

### Post by mishuffs on 2009-02-02
Hello, forget the hard way, try the easy way. after boot from cd or saved ubuntu setup, u will find step 1-3 is so easy. at step 4, select "manual select partition". Than ur drive will be shown. Select a Partion for ubuntu. right click it, make a new small partition for "swap area". From main partition U can break again for making home partition as u like or not. for this choose  /home as the mount point. and now Select Logical, Ext3 format type at format location and set it to use the main partition. Lastly enter the mount point as  /. It is root point. Remember u have to creat 2/3 patition from one patition (no limit actually). I prefer main partition should be ext3 format. go forward. enjoy it.:)

---

