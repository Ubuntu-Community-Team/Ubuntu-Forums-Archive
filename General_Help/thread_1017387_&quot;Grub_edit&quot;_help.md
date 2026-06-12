---
title: "&quot;Grub edit&quot; help"
date: 2008-12-21
forum: General Help
---

### Post by YoungCthulhu on 2008-12-21
Hello,

I have just locked myself out of my computer by playing around with /boot/grub/menu.lst!#-o.  It's a long story, but I have a dual boot ubuntu / xubuntu system, with xubuntu on a usb HDD.  I couldn't get it to work the way I wanted completely and just had to fiddle with something that wasn't really broken, but was annoying the heck out of me all the same on account of I didn't really understand what was going on with how grub works along with the CMOS of the computer.

Anyway, I changed the mount points (?) from (hd0,0) to (hd1,0) to try and stop it from wanting the usbHDD to be turned on every time I booted.  Now all I get when Grub loads is 
grub edit> or something like.  Available commands have been tried but I don't know what I am really doing.  

I got as far as typing in    "load (hd0,0)"  and it responded with "grub loading" and then sent an error message to the effect that I have to load the kernel first.

I am running the latest version of 8.04.  What should I type and in what order to let me get back into my menu.lst and correct all my damage?

Sorry, can't paste from the screen of my machine as I am using my wife's computer.  Fortunately it is an Apple...  bright lady.

Cheers

---

### Post by abhilashm86 on 2008-12-21
> **YoungCthulhu said:**
> Hello,

I have just locked myself out of my computer by playing around with /boot/grub/menu.lst!#-o.  It's a long story, but I have a dual boot ubuntu / xubuntu system, with xubuntu on a usb HDD.  I couldn't get it to work the way I wanted completely and just had to fiddle with something that wasn't really broken, but was annoying the heck out of me all the same on account of I didn't really understand what was going on with how grub works along with the CMOS of the computer.

Anyway, I changed the mount points (?) from (hd0,0) to (hd1,0) to try and stop it from wanting the usbHDD to be turned on every time I booted.  Now all I get when Grub loads is 
grub edit> or something like.  Available commands have been tried but I don't know what I am really doing.  

I got as far as typing in    "load (hd0,0)"  and it responded with "grub loading" and then sent an error message to the effect that I have to load the kernel first.

I am running the latest version of 8.04.  What should I type and in what order to let me get back into my menu.lst and correct all my damage?

Sorry, can't paste from the screen of my machine as I am using my wife's computer.  Fortunately it is an Apple...  bright lady.

Cheers


hey when the GRUB starts u have an option like this

e for edit,b  for boot

u don't touch latest ubuntu,there are other modes,just slide down using down arrow keys,there u press e
e means edit boot option
u can edit the changes,if u messed around,
then u save it,it'll ask
then press b
ubuntu will boot easily

try it n reply,all d best

---

### Post by caljohnsmith on 2008-12-21
In order to get a clearer picture of your setup and menu.lst problem, how about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "boot_info_results.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and what your problem might be.

---

### Post by YoungCthulhu on 2008-12-22
> **caljohnsmith said:**
> In order to get a clearer picture of your setup and menu.lst problem, how about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "boot_info_results.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and what your problem might be.
Thanks Caljohnsmith,

I got my computer working last night, but only by installing another instance of 8.04 on a fresh partition and booting from there.  I tried to get onto the internet and do it your way, but could not get home wifi to work when running from the installation CD even though I checked all the settings multiple times.  Strange that, I have got my Dad's computer to work on an installation CD, but then he's connected via a cable.

Is it possible, via the installation CD, to access the partition that won't boot (hd0,0)?  I couldn't find out how to do it at the command line.

---

### Post by caljohnsmith on 2008-12-22
> **YoungCthulhu said:**
> 
Is it possible, via the installation CD, to access the partition that won't boot (hd0,0)?  I couldn't find out how to do it at the command line.
Yes, (hd0,0) would be sda1, so you should be able to access it by doing:
```
sudo mount /dev/sda1 /mnt
nautilus /mnt &
```
How about trying that and let me know how it goes.

---

### Post by YoungCthulhu on 2008-12-22
> **abhilashm86 said:**
> hey when the GRUB starts u have an option like this

e for edit,b  for boot

u don't touch latest ubuntu,there are other modes,just slide down using down arrow keys,there u press e
e means edit boot option
u can edit the changes,if u messed around,
then u save it,it'll ask
then press b
ubuntu will boot easily

try it n reply,all d best
Thanks for that Abhilashm86,

I couldn't get grub to go as far as the bit you described; I'm afraid my system was too broken at the time! The only option I was presented with was "grub edit>" where you type the boot instructions in longhand.

I did find the correct kernel and initrd settings by booting from an installation disk as caljohnsmith suggests and reading a saved menu.lst file off of a backup disk that I have.  It almost got there but hung finally with the message "kernel panic!" displayed :-) 

Thanks for your help, Abhilashm86 and Caljohnsmith!

---

### Post by YoungCthulhu on 2008-12-23
> **caljohnsmith said:**
> Yes, (hd0,0) would be sda1, so you should be able to access it by doing:
```
sudo mount /dev/sda1 /mnt
nautilus /mnt &
```
How about trying that and let me know how it goes.
Yes that works thanks.  I have ended up with sda1 as my original partition (I guess grub knows that as (hd0,0).  sda2 through to sda5 don't exist, sda6 is the new instance of linux ubuntu 8.04 which I put on last night as a quick and dirty way to get back into my machine, and sda7 is the new swap file for that instance of linux.

I can now boot my machine without having the usb-HDD turned on but this raises several questions:

i)  Is there a simple bash command that I can use that displays partition information?
ii) I have fixed the menu.lst on /boot/grub on sda1.  Since I have installed a new linux partition and it's now working, what on earth is going on??!  (I read that grub takes over from the MBR on the HDD and gets its instructions from /boot/grub/menu.lst, but what menu.lst is it going to?  The one on sda1 or the one on sda6?
iii) This was a crude, dumb and temporary fix by a learner and I want to re-size the second partition sda6 and put xubuntu on it.  This is going to be a pig-pen for me, where I can try out really dumb things and learn faster.  What's the best way of going about this without breaking my main Ubuntu system again?

Thanks for your help once again!
Cheers, and merry Christmas!

---

### Post by neu2buntu on 2008-12-23
```
sudo fdisk -l
``` will show all partitions and also install gparted for resizing partitions ,it is easy to use

```
sudo apt-get install gparted
```

---

### Post by caljohnsmith on 2008-12-23
> **YoungCthulhu said:**
> 
i)  Is there a simple bash command that I can use that displays partition information?

As Chrissy all ready mentioned, you can use:
```
sudo fdisk -l
```
> **YoungCthulhu said:**
> 
ii) I have fixed the menu.lst on /boot/grub on sda1.  Since I have installed a new linux partition and it's now working, what on earth is going on??!  (I read that grub takes over from the MBR on the HDD and gets its instructions from /boot/grub/menu.lst, but what menu.lst is it going to?  The one on sda1 or the one on sda6?

I think the easiest way for you to know which partition controls Grub in the MBR is to run meierfra's script that I gave in post #3; that script will tell you. :)
> **YoungCthulhu said:**
> 
iii) This was a crude, dumb and temporary fix by a learner and I want to re-size the second partition sda6 and put xubuntu on it.  This is going to be a pig-pen for me, where I can try out really dumb things and learn faster.  What's the best way of going about this without breaking my main Ubuntu system again?

Thanks for your help once again!
Cheers, and merry Christmas!
If it's not too much trouble, how about posting the output of meiefra's boot_info_script.txt? That will give me a better picture of your setup so I can help you avoid problems about Grub and such when you go to install other distros like Xubuntu. :)

---

### Post by YoungCthulhu on 2008-12-23
> If it's not too much trouble, how about posting the output of meiefra's boot_info_script.txt? That will give me a better picture of your setup so I can help you avoid problems about Grub and such when you go to install other distros like Xubuntu.

Thanks caljohnsmith, I am at the office at the moment, but will do that when I get home.  I can't download or run anything here without admin rights on this Windows workstation.  :-(

Cheers

---

### Post by YoungCthulhu on 2008-12-24
Gidday Caljohnsmith,

Here 'tis.

Cheers and merry Christmas!  :popcorn:

---

### Post by caljohnsmith on 2008-12-24
Hi Stuart, it doesn't look like the RESULTS.txt file was successfully attached to your last post. How about opening up the RESULTS.txt file in a text editor, and simply copying/pasting the text into your next post, if that's OK. :)

---

### Post by DWade on 2008-12-26
I am going to put my three cents in here.

1st the quickest way to fix grub, is to get your installation cd's
#1 the desktop version which is a live cd an the second most important one
the alternate install cd.

Using the desktop cd open up sda1 with nautilus (your file browser) and delete all menu.lst including the backup copies

exit and put in the alternate cd and boot to it.

when the grub boot menu comes up select fix broken system should be item number 4

follow all prompts until it ask where your system is and select that partition,
it will look like this
/dev/sda1
/dev/sda2
/dev/sda3
/dev/sda5
/dev/sda6

move the cursor to /dev/sda1  hit enter
you will get a menu
select
    reinstall grub boot loader

since you are I believe using all linux, in the command line type
/dev/sda  or (hd0)
this will place grub in you MBR and reinitialize all of boot options

This should work perfectly unless you edited a file in /etc /sbin

I keep hoping they will make a boot up cd just to reinstall grub, and not having to go thru the time it takes to get to that prompt.

Have a nice day

---

### Post by ispy on 2008-12-26
Or try the Supergrub Live CD

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by YoungCthulhu on 2008-12-28
Here it is, it's gonna be a big-un...

> Grub is installed in the MBR of /dev/sda and looks on the same drive in partition #6 for its boot files.

sda1:
    File system:  ext3
    Boot sector  type:  No Boot Loader
    Boot sector  info:  
    Operating System: Ubuntu 8.04.1 \n \l
    Boot files/directories present:  /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda2:
    File system:  Extended Partition

sda5:
    File system:  swap

sda6:
    File system:  ext3
    Boot sector  type:  No Boot Loader
    Boot sector  info:  
    Operating System: Ubuntu 8.04 \n \l
    Boot files/directories present:  /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda7:
    File system:  swap


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x83a183a1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    97610939    48805438+  83  Linux
/dev/sda2        97610940   312576704   107482882+   5  Extended
/dev/sda5       300415563   312576704     6080571   82  Linux swap / Solaris
/dev/sda6        97611066   292077764    97233349+  83  Linux
/dev/sda7       292077828   300415499     4168836   82  Linux swap / Solaris

Partition table entries are not in disk order

Warning: partition 5 does not start at a cylinder boundary

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-22-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/stuart/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=stuart)

/dev/sda1: UUID="ef2a1585-512e-49b5-bfc4-5791ed16bf1c" TYPE="ext3" 
/dev/sda5: UUID="7aadcff0-b873-4727-be89-073d27a7dfbc" TYPE="swap" 
/dev/sda6: UUID="79e977da-6ead-417d-8ff7-03cf268b2e6e" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: TYPE="swap" UUID="f716798c-4787-40fa-9e5d-2ad1afd3f2ea" 

sda1/boot/grub/menu.lst

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
default		saved

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		15

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=ef2a1585-512e-49b5-bfc4-5791ed16bf1c ro

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
# lockalternative=true

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=splash vga=799

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
# savedefault=true

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=ef2a1585-512e-49b5-bfc4-5791ed16bf1c ro splash vga=799
initrd		/boot/initrd.img-2.6.24-22-generic
quiet
savedefault

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
lock
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=ef2a1585-512e-49b5-bfc4-5791ed16bf1c ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=ef2a1585-512e-49b5-bfc4-5791ed16bf1c ro splash vga=799
initrd		/boot/initrd.img-2.6.24-21-generic
quiet
savedefault

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
lock
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=ef2a1585-512e-49b5-bfc4-5791ed16bf1c ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=ef2a1585-512e-49b5-bfc4-5791ed16bf1c ro splash vga=799
initrd		/boot/initrd.img-2.6.24-19-generic
quiet
savedefault

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
lock
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=ef2a1585-512e-49b5-bfc4-5791ed16bf1c ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=ef2a1585-512e-49b5-bfc4-5791ed16bf1c ro splash vga=799
initrd		/boot/initrd.img-2.6.24-18-generic
quiet
savedefault

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic (recovery mode)
lock
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=ef2a1585-512e-49b5-bfc4-5791ed16bf1c ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=ef2a1585-512e-49b5-bfc4-5791ed16bf1c ro splash vga=799
initrd		/boot/initrd.img-2.6.24-16-generic
quiet
savedefault

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
lock
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=ef2a1585-512e-49b5-bfc4-5791ed16bf1c ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

sda1/etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=ef2a1585-512e-49b5-bfc4-5791ed16bf1c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=7aadcff0-b873-4727-be89-073d27a7dfbc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

sda1/boot

total 89808
drwxr-xr-x  3 root root    4096 2008-12-08 21:35 .
drwxr-xr-x 21 root root    4096 2008-12-22 21:56 ..
-rw-r--r--  1 root root  422607 2008-04-11 02:51 abi-2.6.24-16-generic
-rw-r--r--  1 root root  422667 2008-05-29 12:39 abi-2.6.24-18-generic
-rw-r--r--  1 root root  422667 2008-08-21 14:46 abi-2.6.24-19-generic
-rw-r--r--  1 root root  422838 2008-10-22 14:12 abi-2.6.24-21-generic
-rw-r--r--  1 root root  422838 2008-11-25 09:47 abi-2.6.24-22-generic
-rw-r--r--  1 root root   79964 2008-04-11 02:51 config-2.6.24-16-generic
-rw-r--r--  1 root root   80071 2008-05-29 12:39 config-2.6.24-18-generic
-rw-r--r--  1 root root   80049 2008-08-21 14:46 config-2.6.24-19-generic
-rw-r--r--  1 root root   80062 2008-10-22 14:12 config-2.6.24-21-generic
-rw-r--r--  1 root root   80062 2008-11-25 09:47 config-2.6.24-22-generic
drwxr-xr-x  3 root root    4096 2008-12-22 23:43 grub
-rw-r--r--  1 root root 7493375 2008-10-02 20:06 initrd.img-2.6.24-16-generic
-rw-r--r--  1 root root 7493708 2008-08-15 20:18 initrd.img-2.6.24-16-generic.bak
-rw-r--r--  1 root root 7495021 2008-10-02 20:06 initrd.img-2.6.24-18-generic
-rw-r--r--  1 root root 7495234 2008-08-15 20:18 initrd.img-2.6.24-18-generic.bak
-rw-r--r--  1 root root 7494628 2008-10-02 20:05 initrd.img-2.6.24-19-generic
-rw-r--r--  1 root root 7495153 2008-09-01 20:01 initrd.img-2.6.24-19-generic.bak
-rw-r--r--  1 root root 7496415 2008-11-08 18:46 initrd.img-2.6.24-21-generic
-rw-r--r--  1 root root 7496344 2008-10-29 20:13 initrd.img-2.6.24-21-generic.bak
-rw-r--r--  1 root root 7494573 2008-12-08 21:35 initrd.img-2.6.24-22-generic
-rw-r--r--  1 root root 7494574 2008-12-02 01:40 initrd.img-2.6.24-22-generic.bak
-rw-r--r--  1 root root  103204 2007-09-28 20:06 memtest86+.bin
-rw-r--r--  1 root root  899892 2008-04-11 02:51 System.map-2.6.24-16-generic
-rw-r--r--  1 root root  905012 2008-05-29 12:39 System.map-2.6.24-18-generic
-rw-r--r--  1 root root  905170 2008-08-21 14:46 System.map-2.6.24-19-generic
-rw-r--r--  1 root root  905617 2008-10-22 14:12 System.map-2.6.24-21-generic
-rw-r--r--  1 root root  905617 2008-11-25 09:47 System.map-2.6.24-22-generic
-rw-r--r--  1 root root 1904248 2008-04-11 02:51 vmlinuz-2.6.24-16-generic
-rw-r--r--  1 root root 1921528 2008-05-29 12:39 vmlinuz-2.6.24-18-generic
-rw-r--r--  1 root root 1921464 2008-08-21 14:46 vmlinuz-2.6.24-19-generic
-rw-r--r--  1 root root 1920760 2008-10-22 14:12 vmlinuz-2.6.24-21-generic
-rw-r--r--  1 root root 1921176 2008-11-25 09:47 vmlinuz-2.6.24-22-generic

sda1/boot/grub

total 232
drwxr-xr-x 3 root root   4096 2008-12-22 23:43 .
drwxr-xr-x 3 root root   4096 2008-12-08 21:35 ..
-rw-r--r-- 1 root root    197 2008-06-09 17:38 default
-rw-r--r-- 1 root root     15 2008-06-09 17:38 device.map
-rw-r--r-- 1 root root   8056 2008-06-09 17:38 e2fs_stage1_5
-rw-r--r-- 1 root root   7904 2008-06-09 17:38 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-06-09 17:38 installed-version
-rw-r--r-- 1 root root   8608 2008-06-09 17:38 jfs_stage1_5
-rw-r--r-- 1 root root   6095 2008-12-21 09:40 menu.lst
-rw-r--r-- 1 root root   6095 2008-12-21 09:40 menu.lst~
-rw-r--r-- 1 root root   5135 2008-08-15 20:16 menu.lst.backup
-rw-r--r-- 1 root root   6095 2008-12-21 15:03 menu.lst.sus
-rw-r--r-- 1 root root   7324 2008-06-09 17:38 minix_stage1_5
-rw-r--r-- 1 root root   9632 2008-06-09 17:38 reiserfs_stage1_5
drwxr-xr-x 2 root root   4096 2008-08-15 20:16 splashimages
-rw-r--r-- 1 root root    512 2008-06-09 17:38 stage1
-rw-r--r-- 1 root root 108356 2008-06-09 17:38 stage2
-rw-r--r-- 1 root root   9276 2008-06-09 17:38 xfs_stage1_5

sda6/boot/grub/menu.lst

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
# kopt=root=UUID=79e977da-6ead-417d-8ff7-03cf268b2e6e ro

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=79e977da-6ead-417d-8ff7-03cf268b2e6e ro quiet splash
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=79e977da-6ead-417d-8ff7-03cf268b2e6e ro single

title		Ubuntu 8.04, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=ef2a1585-512e-49b5-bfc4-5791ed16bf1c ro splash vga=799 
initrd		/boot/initrd.img-2.6.24-22-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=ef2a1585-512e-49b5-bfc4-5791ed16bf1c ro single 
initrd		/boot/initrd.img-2.6.24-22-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=ef2a1585-512e-49b5-bfc4-5791ed16bf1c ro splash vga=799 
initrd		/boot/initrd.img-2.6.24-21-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=ef2a1585-512e-49b5-bfc4-5791ed16bf1c ro single 
initrd		/boot/initrd.img-2.6.24-21-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=ef2a1585-512e-49b5-bfc4-5791ed16bf1c ro splash vga=799 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=ef2a1585-512e-49b5-bfc4-5791ed16bf1c ro single 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.1, kernel 2.6.24-18-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=ef2a1585-512e-49b5-bfc4-5791ed16bf1c ro splash vga=799 
initrd		/boot/initrd.img-2.6.24-18-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.1, kernel 2.6.24-18-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=ef2a1585-512e-49b5-bfc4-5791ed16bf1c ro single 
initrd		/boot/initrd.img-2.6.24-18-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=ef2a1585-512e-49b5-bfc4-5791ed16bf1c ro splash vga=799 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=ef2a1585-512e-49b5-bfc4-5791ed16bf1c ro single 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04.1, memtest86+ (on /dev/sda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


sda6/etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=79e977da-6ead-417d-8ff7-03cf268b2e6e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=f716798c-4787-40fa-9e5d-2ad1afd3f2ea none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

sda6/boot

total 10564
drwxr-xr-x  3 root root    4096 2008-12-22 23:35 .
drwxr-xr-x 21 root root    4096 2008-12-22 23:34 ..
-rw-r--r--  1 root root  422607 2008-04-11 02:51 abi-2.6.24-16-generic
-rw-r--r--  1 root root   79964 2008-04-11 02:51 config-2.6.24-16-generic
drwxr-xr-x  2 root root    4096 2008-12-22 23:35 grub
-rw-r--r--  1 root root 7349268 2008-04-23 04:00 initrd.img-2.6.24-16-generic.bak
-rw-r--r--  1 root root  103204 2007-09-28 20:06 memtest86+.bin
-rw-r--r--  1 root root  899892 2008-04-11 02:51 System.map-2.6.24-16-generic
-rw-r--r--  1 root root 1904248 2008-04-11 02:51 vmlinuz-2.6.24-16-generic

sda6/boot/grub

total 204
drwxr-xr-x 2 root root   4096 2008-12-22 23:35 .
drwxr-xr-x 3 root root   4096 2008-12-22 23:35 ..
-rw-r--r-- 1 root root    197 2008-12-22 23:35 default
-rw-r--r-- 1 root root     15 2008-12-22 23:35 device.map
-rw-r--r-- 1 root root   8056 2008-12-22 23:35 e2fs_stage1_5
-rw-r--r-- 1 root root   7904 2008-12-22 23:35 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-22 23:35 installed-version
-rw-r--r-- 1 root root   8608 2008-12-22 23:35 jfs_stage1_5
-rw-r--r-- 1 root root   8084 2008-12-22 23:35 menu.lst
-rw-r--r-- 1 root root   7324 2008-12-22 23:35 minix_stage1_5
-rw-r--r-- 1 root root   9632 2008-12-22 23:35 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-22 23:35 stage1
-rw-r--r-- 1 root root 108356 2008-12-22 23:35 stage2
-rw-r--r-- 1 root root   9276 2008-12-22 23:35 xfs_stage1_5

StdErr Messages 



Cheers

---

### Post by caljohnsmith on 2008-12-28
Thanks for posting the output of the script, that clarifies your setup quite a bit. So looking at your sda1 Ubuntu menu.lst, it looks OK to me at this point, so if you reinstall Grub to the MBR (Master Boot Record) of your sda drive so that it points to your sda1 partition instead of your sda6 partition, I think that should fix the problem. How about on start up when you get the grub menu, press "c" to get the command line, and then do:
```
grub> root (hd0,0)
grub> setup (hd0)
```
And then press "Ctrl-Alt-Delete" to reboot, and you should get your sda1 Ubuntu Grub menu. Also, you said you had Xubuntu on your USB drive, but was that drive disconnected when you ran the script? Because the script doesn't show any drives other than your sda drive. 

And lastly, if the above steps work and you decide to install Xubuntu to your sda6 partition, I would recommend clicking the "advanced" button near the end of the Xubuntu installer process, and specify to have Grub installed to /dev/sda6 which is the boot sector of the soon-to-be Xubuntu partition, rather than /dev/sda or (hd0) which is the MBR. That way Ubuntu on sda1 will stay in charge of the booting process. Anyway, let me know how it goes or if you run into problems. :)

---

### Post by YoungCthulhu on 2008-12-29
> **caljohnsmith said:**
> Thanks for posting the output of the script, that clarifies your setup quite a bit. So looking at your sda1 Ubuntu menu.lst, it looks OK to me at this point, so if you reinstall Grub to the MBR (Master Boot Record) of your sda drive so that it points to your sda1 partition instead of your sda6 partition, I think that should fix the problem. How about on start up when you get the grub menu, press "c" to get the command line, and then do:
```
grub> root (hd0,0)
grub> setup (hd0)
```
And then press "Ctrl-Alt-Delete" to reboot, and you should get your sda1 Ubuntu Grub menu. Also, you said you had Xubuntu on your USB drive, but was that drive disconnected when you ran the script? Because the script doesn't show any drives other than your sda drive. 

And lastly, if the above steps work and you decide to install Xubuntu to your sda6 partition, I would recommend clicking the "advanced" button near the end of the Xubuntu installer process, and specify to have Grub installed to /dev/sda6 which is the boot sector of the soon-to-be Xubuntu partition, rather than /dev/sda or (hd0) which is the MBR. That way Ubuntu on sda1 will stay in charge of the booting process. Anyway, let me know how it goes or if you run into problems. :)
Thanks for that!  It worked.  I guess fdisk -l shows the offending settings, namely that grub was looking for the MBR on sda6.  Now, running fdisk from a terminal yields:
> 
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x83a183a1
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6076    48805438+  83  Linux
/dev/sda2            6077       19457   107482882+   5  Extended
/dev/sda5           18701       19457     6080571   82  Linux swap / Solaris
/dev/sda6           18182       18700     4168836   82  Linux swap / Solaris


I want to install Xubuntu on my usbHDD, it has 500GB capacity and I want to do all my messing around learning how to bash script etc **_there_** (points across at usbHDD box atop computer box), rather than over **_here_** (points down at desk surface, under screen), where all my photos and music are stored  :-)

Cheers and happy new year

---

### Post by YoungCthulhu on 2008-12-29
> **neu2buntu said:**
> ```
sudo fdisk -l
``` will show all partitions and also install gparted for resizing partitions ,it is easy to use

```
sudo apt-get install gparted
```
Thanks for that advice. I have downloaded gparted and am working out how to use it, to claim back my lost disk space taken up by sda5 and sda6.  I'll let you know how I get on...

Cheers

---

