---
title: "creating a grub configuration file"
date: 2009-05-20
forum: General Help
---

### Post by vegolord on 2009-05-20
hi to everybody
 
i am new to ubuntu and i am trying to create a configuration file menu.lst for using both ubuntu and windows...but i have some problems...
this is the partition i would like to create....
 
Device System
/dev/sda1 Linux System
/dev/sda2 Linux swap
/dev/sda3 Linux (/home)
/dev/sdb1 Windows System
/dev/sdb2 Windows data
 
thanks to everybody....

---

### Post by spacesamurai on 2009-05-20
Could you please clarify. Are the partitions you mentioned already made and you just want to set up the grub so that you can boot? Or is it that you want to actually make the partitions?

---

### Post by vegolord on 2009-05-20
i would like to make that partition...i have nothing installed and i am trying to understand and to use grub....
thanks

---

### Post by mcduck on 2009-05-20
> **vegolord said:**
> i would like to make that partition...i have nothing installed and i am trying to understand and to use grub....
thanks

Grub isn't the tool for creating partitions. It simply offers a menu to boot from existing partitions.

If you need to actually create partitions I recommend installing gparted (it's also included on the Ubuntu CD so you can use it directly from the live environment).

Anyway, if you have now nothing installed then just install Windows first like you would normally do, and let it create it's own partitions. Leave the space you want to use for Linux partitions as empty, unpartitioned space.

After that start the Ubuntu installer, and use it to create the partitions you want for Ubuntu.

Ubuntu's installer will automatically configure Grub for you and add options to boot both Ubuntu & Windows.

---

### Post by vegolord on 2009-05-20
yes ,  but i just need to see how the menu.lst for this partition is: i have intalled only ubuntu on my pc and right now i just want to create the idea of the configuration file only....is it possible just to create this file without installing windows.( just the file menu.lst)
 
thanks a lot

---

### Post by spacesamurai on 2009-05-20
I might not understand your question properly, but if you have installed Ubuntu and you want to change the grub to include Windows (as if it was installed), then yes, you could do it.

> 
title Ubuntu, kernel ####
uuid		<UUID>
kernel		/vmlinuz-2.6.28-11-generic root=<UUID> ro quiet splash 
initrd		/initrd.img-2.6.28-11-generic
quiet


title No good Windows
root (hd1,0)
savedefault
makeactive
chainloader +1


Note the UUID. Ubuntu has aldeay configured this, so you do not have to worry about what slice and what drive. You could also designate the logcial device name at (root=<UUID>)

Hope this helps

---

### Post by mcduck on 2009-05-20
In that case the windows entry in menu.lst would be something like this:
```
title       Windows
rootnoverify (hd1,0)
makeactive
chainloader +1
```

Sometimes Windows has problems booting if it's not on the first partition of first hard disk. In that case you can use entry like this to make Windows believe it's partition is the first one:
```
title       Windows
rootnoverify (hd0,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1
```

The Windows entry can be pretty much anywhere in the file, as long as you keep it outside of the section marked as "debian automagic kernels list". Simply adding the Windows entry to the end of the file works fine.

You can add the entry to menu.lst even if such partition/drive doesn't exist, but trying to boot from it will of course just result in error.

---

### Post by vegolord on 2009-05-20
thankyou very much for your time....i am at the begining with ubuntu and in general with linux...
 
i just write this code and i would like to know if is good for my partition... i just want a file menu.lst that is good for the partition i want to create......
 
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
default  0
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout  20
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
# title  Windows 95/98/NT/2000
# root  (hd0,0)
# makeactive
# chainloader +1
#
# title  Linux
# root  (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
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
# kopt=root=/dev/hda5 ro
## default grub root device
## e.g. groot=(hd0,0)
groot=(sd0,4)
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
# defoptions=
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
# altoptions=(single-user mode) single
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
title  Ubuntu kernel 2.6.18-6-686
root  (sd0,4)
kernel  /boot/vmlinuz-2.6.28-11 root=/dev/sda1 ro 
initrd  /boot/initrd.img-2.6.18-6-686
savedefault
title  Ubuntu kernel 2.6.18-6-686(single-user mode)
root  (sd0,4)
kernel  /boot/vmlinuz-2.6.18-6-686 root=/dev/sda1 ro single
initrd  /boot/initrd.img-2.6.18-6-686
savedefault
### END DEBIAN AUTOMAGIC KERNELS LIST
# This is a divider, added to separate the menu items below from the Debian
# ones.
title  Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title  Microsoft Windows XP Professional
root  (hd1,0)
savedefault
makeactive
chainloader +1
 

```

---

### Post by spacesamurai on 2009-05-20
That may work. After seeing your main.lst, thought, the type of hard disk may be incorrect.

You might want to change as follows:

Before)
root  (hd1,0) 

After)
root  (sd1,0)

---

### Post by mcduck on 2009-05-20
> **spacesamurai said:**
> That may work. After seeing your main.lst, thought, the type of hard disk may be incorrect.

You might want to change as follows:

Before)
root  (hd1,0) 

After)
root  (sd1,0)
While *Linux* names the drives depending on the type of the drive (or at least used to, before they started using SATA/SCSI drivers for PATA drives as well), *Grub* doesn't.

Grub uses hdX,X syntax for all drives/partitions. It makes no difference if it's PATA, SATA or SCSI drive.

---

### Post by vegolord on 2009-05-20
so you think this code may work for this partition...
 
Device      System
/dev/sda1 Linux System
/dev/sda2 Linux swap
/dev/sda3 Linux (/home)
/dev/sdb1 Windows System
/dev/sdb2 Windows data
 
after 20 sec it loads ubuntu and it is possible to select windows
 
 
 
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
default  0
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout  20
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
# title  Windows 95/98/NT/2000
# root  (hd0,0)
# makeactive
# chainloader +1
#
# title  Linux
# root  (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
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
# kopt=root=/dev/hda5 ro
## default grub root device
## e.g. groot=(hd0,0)
groot=(sd0,4)
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
# defoptions=
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
# altoptions=(single-user mode) single
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
title  Ubuntu kernel 2.6.18-6-686
root  (sd0,4)
kernel  /boot/vmlinuz-2.6.28-11 root=/dev/sda1 ro 
initrd  /boot/initrd.img-2.6.18-6-686
savedefault
title  Ubuntu kernel 2.6.18-6-686(single-user mode)
root  (sd0,4)
kernel  /boot/vmlinuz-2.6.18-6-686 root=/dev/sda1 ro single
initrd  /boot/initrd.img-2.6.18-6-686
savedefault
### END DEBIAN AUTOMAGIC KERNELS LIST
# This is a divider, added to separate the menu items below from the Debian
# ones.
title  Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title  Microsoft Windows XP Professional
root  (sd1,0)
savedefault
makeactive
chainloader +1

```

---

### Post by mcduck on 2009-05-20
> **vegolord said:**
> so you think this code may work for this partition...
 
Device      System
/dev/sda1 Linux System
/dev/sda2 Linux swap
/dev/sda3 Linux (/home)
/dev/sdb1 Windows System
/dev/sdb2 Windows data
 
after 20 sec it loads ubuntu and it is possible to select windows
 
 
 
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
default  0
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout  20
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
# title  Windows 95/98/NT/2000
# root  (hd0,0)
# makeactive
# chainloader +1
#
# title  Linux
# root  (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
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
# kopt=root=/dev/hda5 ro
## default grub root device
## e.g. groot=(hd0,0)
groot=(sd0,4)
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
# defoptions=
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
# altoptions=(single-user mode) single
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
title  Ubuntu kernel 2.6.18-6-686
root  (sd0,4)
kernel  /boot/vmlinuz-2.6.28-11 root=/dev/sda1 ro 
initrd  /boot/initrd.img-2.6.18-6-686
savedefault
title  Ubuntu kernel 2.6.18-6-686(single-user mode)
root  (sd0,4)
kernel  /boot/vmlinuz-2.6.18-6-686 root=/dev/sda1 ro single
initrd  /boot/initrd.img-2.6.18-6-686
savedefault
### END DEBIAN AUTOMAGIC KERNELS LIST
# This is a divider, added to separate the menu items below from the Debian
# ones.
title  Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title  Microsoft Windows XP Professional
root  (sd1,0)
savedefault
makeactive
chainloader +1

```

Couple of problems there:

1. Grub uses "hdX" naming for all hard drives, and "hdX,X" for all partitions. It makes no difference if it's SATA, SCSI or PATA drive.

2. Your Linux boot settings specify root partition to be hd0,4 (which would be fifth partition on first hard drive). On the other hand, kernel options specify root partition to be in /dev/sda1 which is first partition of first hard disk.. Obviously they should be same. If the Linux root partition is first partition of first hard drive, set the root to hd0,0.

---

### Post by vegolord on 2009-05-20
yes, you are right...thanks
 
Device System
/dev/sda1 Linux System
/dev/sda2 Linux swap
/dev/sda3 Linux (/home)
/dev/sdb1 Windows System
/dev/sdb2 Windows data
 
ok and now it should be ok?
 
 
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
default  0
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout  30
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
# title  Windows 95/98/NT/2000
# root  (hd0,0)
# makeactive
# chainloader +1
#
# title  Linux
# root  (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
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
# kopt=root=/dev/hda5 ro
## default grub root device
## e.g. groot=(hd0,0)
groot=(sd0,4)
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
# defoptions=
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
# altoptions=(single-user mode) single
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
 
title  Ubuntu kernel 2.6.18-6-686
root  (sd0,0)
kernel  /boot/vmlinuz-2.6.28-11 root=/dev/sda1 ro 
initrd  /boot/initrd.img-2.6.18-6-686
savedefault
 
title  Ubuntu kernel 2.6.18-6-686(single-user mode)
root  (sd0,0)
kernel  /boot/vmlinuz-2.6.18-6-686 root=/dev/sda1 ro single
initrd  /boot/initrd.img-2.6.18-6-686

savedefault
### END  AUTOMAGIC KERNELS LIST
# This is a divider, added to separate the menu items below from the Debian
# ones.
title  Other operating systems:
root

# This entry automatically added by the  installer for a non-linux OS
# on /dev/
title  Microsoft Windows XP Professional
root  (sd1,0)
savedefault
makeactive
chainloader +1
 

```

---

