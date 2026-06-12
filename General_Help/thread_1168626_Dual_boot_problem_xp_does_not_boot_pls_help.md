---
title: "Dual boot problem xp does not boot pls help"
date: 2009-05-24
forum: General Help
---

### Post by Pablo M. on 2009-05-24
i tried to doal boot windows xp pro and linux iv had so many problems like grub error 22 and many more but i was able to fix those and everything was working fine i could boot into everything and it was all working great. but now i have a new problem when i start my computer and it gives me the option of booting to (Ubuntu 9.04, kernel 2.6.28-11-generic), (Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)), (Ubuntu 9.04, memtest86+), and (Microsoft Windows XP Professional) i can boot into all of them exept windows. at first it gave me error 13: unexecutable format but then i edited the menu.lst and boot.ini and it doesnt give me the error but it says starting up ... and nothing happens it does not start up. 
this is my menu.lst
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
default        0


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
# title        Windows 95/98/NT/2000
# root        (hd1,0)
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
# kopt=root=UUID=d28659fe-0902-461b-b97a-04d2493cfe32 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d28659fe-0902-461b-b97a-04d2493cfe32

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        d28659fe-0902-461b-b97a-04d2493cfe32
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=d28659fe-0902-461b-b97a-04d2493cfe32 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        d28659fe-0902-461b-b97a-04d2493cfe32
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=d28659fe-0902-461b-b97a-04d2493cfe32 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        d28659fe-0902-461b-b97a-04d2493cfe32
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd1,0)
savedefault
makeactive
chainloader    +1
```my boot.ini
```
[boot loader] 
timeout=5 
default=multi(0)disk(1)rdisk(0)partition(0)\WINDOWS 
[operating systems] 
multi(0)disk(1)rdisk(1)partition(0)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
```i have 2 hds one is bout 40 gb its were i installed ubuntu
my other hd is160gb partitiond in two 1st partition is 37gb and its where windows is installed the second partition is 110 gb and both are ntfs partitions
i would realy appreciate urgent help

---

### Post by lindsay7 on 2009-05-24
You need to map the drive in the grub menu it should look like this is you are correct with the partition numbers


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader    +1


Do this and see it that fixes things. We may need to fix you grub menu too and or the windows mbr. Let me know.

To get in you grub menu type "sudo gedit /boot/grub/menu.lst"
add the lines I gave you and save the file. Do not change anything else.


In case Ubuntu does not start do this, type in the terminal

Sudo grub
find /boot/grub/stage1
(it will give a (hdx,y)
root (hdx,y)
setup(hdx)
quit


and the last thing to work on, if windows does not boot use this to get your windows mbr back, note is you use this to do so, you will most likely need to run the sudo grub commands again because redoing the mbr normally wipes out the grub file.

Type in the terminal "sudo apt-get install lilo" then "sudo lilo -M /dev/sda mbr" , this will reset your windows mbr and boot windows.  sda is the same as hd0.

---

### Post by Pablo M. on 2009-05-25
ok my problem just got more complicated..... unfortunately before i read ur reply i tried to reinstall windows and it wasnt working so i went into ubuntu partition editor and deleted the second ntfs partition on my 160gb hd (not the partition windows was installed in). at least ubuntu still works. i did everything that u said and when i chose windows it brings up a new menu where i choose defult xp or xp professional iv tried it as well as the f8 advanced menu but they all lead me to a screen which says
> windows could not start because of a computer disk hardware config. problem.could not read from selected boot disk. check boot path and disk hardware.pls check the windows documentation about hardware disk config. and your hareware reference manuals for additional info.i realy apreciate you help becaue im in realy desprate sircumstances
>  im leaving to someware els in a 6 of days and im testing out linux xp dual boot on my pc to see if i should do it in my laptop but i wana be able to fix the problems myself. only reason i still have windows is games. anyways i need to fix this so when i leave my fam can still use the pc. and to make things worse i have final exams wich i got to study for so this is taking up valuable study time... if u can provide an answer i would realy be glad if not ill just tell my family to have a pro reinstall windows becaue they dont know how 2 use ubuntu... and i dont think they are willing 2 learn.
anyways thenks for the help im realy impressed with ubuntu linux and even that i got a reply within an hour stupid me that i didnt check before trying anything stupid.....

---

### Post by lindsay7 on 2009-05-25
Try this to see if it will fix you windows booting problem.  Run this command usint the windows install disk repair option, command propt.

The device (drive) on which you want to write a new master boot record. The name can be obtained from the output of the map command. An example of a device name is:

\Device\HardDisk0.

Example

The following example writes a new master boot record to the device specified:

fixmbr \Device\HardDisk0

If you just type fixmbr it will try to fix the disk where windows is located by default.



If that does not work then run the repair option using the windows install disk.


If none of this works and you are willing to install windows again. You could delete both windows partions or reformat them and install windows again. Please note that doing the above fixs and or installing windows again may mess up you Ubuntu booting and you will have to run the Sudo grub list of commands again.

---

### Post by Pablo M. on 2009-05-25
ok thenks allot ill try it. but im not sure i have the instalation cd i have the windows OEM preinstallation kit and sp2 but how could i use that to fix this? it sends me to system32 cmp.exe its like comand prompt how do i fix my problem with this cd? If u have solution pls be specific. like do i boot from the cd?

anywasy i realy apreciate the help!
thenks allot hope i dont wast to much of your time.

---

### Post by lindsay7 on 2009-05-25
In post #3 you said you tried to reinstall windows so I thought you had the disk to do this. Yes you would boot from this disk. It will give you the option to install Windows or do a repair. When you choose repair, you can run a repair or you can get to a command prompt.

---

### Post by Pablo M. on 2009-05-26
ok thenks allot.

---

