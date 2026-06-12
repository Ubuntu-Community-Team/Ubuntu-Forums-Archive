---
title: "Grub cannot see Vista"
date: 2009-03-24
forum: General Help
---

### Post by sunseeker888 on 2009-03-24
Hello

once i installed ubuntu, now in the grub menu, vista does not appear, but it's definitely there


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


fdisk -l output


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1337    10732544   27  Unknown
/dev/sda2   *        1337       24442   185588916    7  HPFS/NTFS
/dev/sda3           24443       30401    47865667+  83  Linux








I am a newbie in Ubuntu, i do not know what to change in Grub.lst above, do not understand hd0,1 is linux, but hd0,0 is vista, but it's loading linux first which according to fdisk, linix is hd0,2? Am i correct

can somebody edit the above menu.lst for me please. I am really desperate, this my new laptop for a week. I really to migrate to ubuntu




Thanks in advance

S888

---

### Post by bruno9779 on 2009-03-24
Vista only works if you installed ubuntu through Wubi

---

### Post by James_Lochhead on 2009-03-24
> **bruno9779 said:**
> Vista only works if you installed ubuntu through Wubi

That is complete rubbish.

Vista will work properly if you do a normal Ubuntu install through the live cd. Installing this way is actually more common than Wubi.

Grub config is kept in the file /boot/grub/menu.1st.

Open a terminal and type gksudo gedit /boot/grub/menu.1st and take a look. Scroll to the bottom of the file. There will be grub entries like this:

```

title		Continue Start-up
uuid		86c6366c-dde0-4040-8ccf-68ee1df1e6c4
kernel		/vmlinuz-2.6.27-11-generic root=/dev/mapper/lvm-root--partition ro quiet splash 
initrd		/initrd.img-2.6.27-11-generic
quiet

```

Note: In yours Continue Start-up will be something like Ubuntu 8.10 kernel etc...

Below this should be something similarly formatted with a title involving vista and (hd0,0) etc

If it is not there you need to add it.

---

### Post by philinux on 2009-03-24
> **sunseeker888 said:**
> Hello

once i installed ubuntu, now in the grub menu, vista does not appear, but it's definitely there


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


fdisk -l output


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1337    10732544   27  Unknown
/dev/sda2   *        1337       24442   185588916    7  HPFS/NTFS
/dev/sda3           24443       30401    47865667+  83  Linux








I am a newbie in Ubuntu, i do not know what to change in Grub.lst above, do not understand hd0,1 is linux, but hd0,0 is vista, but it's loading linux first which according to fdisk, linix is hd0,2? Am i correct

can somebody edit the above menu.lst for me please. I am really desperate, this my new laptop for a week. I really to migrate to ubuntu




Thanks in advance

S888

when the grub menu appears press esc. Then use the down arrow key to highlight the vista line and press enter to boot vista.

---

### Post by James_Lochhead on 2009-03-24
We can make it easier for you. But we do not have enough of menu.1st. The part you posted is just comments. Post more and we can edit it.

---

### Post by sunseeker888 on 2009-03-24
> **James_Lochhead said:**
> We can make it easier for you. But we do not have enough of menu.1st. The part you posted is just comments. Post more and we can edit it.



my apologies

here the full output
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
# kopt=root=UUID=77dae542-a37f-4518-b13e-ef7abc61fc40 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=77dae542-a37f-4518-b13e-ef7abc61fc40

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
uuid		77dae542-a37f-4518-b13e-ef7abc61fc40
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=77dae542-a37f-4518-b13e-ef7abc61fc40 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		77dae542-a37f-4518-b13e-ef7abc61fc40
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=77dae542-a37f-4518-b13e-ef7abc61fc40 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		77dae542-a37f-4518-b13e-ef7abc61fc40
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=77dae542-a37f-4518-b13e-ef7abc61fc40 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		77dae542-a37f-4518-b13e-ef7abc61fc40
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=77dae542-a37f-4518-b13e-ef7abc61fc40 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		77dae542-a37f-4518-b13e-ef7abc61fc40
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```



Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbd1a0e96

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1337    10732544   27  Unknown
/dev/sda2   *        1337       24442   185588916    7  HPFS/NTFS
/dev/sda3           24443       30401    47865667+  83  Linux

Disk /dev/sdb: 2199.0 GB, 2199023185920 bytes
255 heads, 63 sectors/track, 267349 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System

---

### Post by mhgsys on 2009-03-24
Ok, 
what happens if you add ```


title Windows Vista
root (hd0,1)
chainloader +1


```

 to /boot/grub/menu.lst

(to do this open a terminal and type)
```

sudo nano /boot/grub/menu.lst

```

---

### Post by tchoklat on 2009-03-24
Add the following atfer ### END DEBIAN AUTOMAGIC KERNELS LIST
 
title Windows 95/98/NT/2000
root (hd0,1)
makeactive
chainloader +1
 
This will give the option of starting windows from grub ...

---

### Post by James_Lochhead on 2009-03-24
The previous post should solve your problem.

Additionally:

```

title Ubuntu 8.10, kernel 2.6.27-7-generic
uuid 77dae542-a37f-4518-b13e-ef7abc61fc40
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=77dae542-a37f-4518-b13e-ef7abc61fc40 ro quiet splash
initrd /boot/initrd.img-2.6.27-7-generic
quiet

title Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid 77dae542-a37f-4518-b13e-ef7abc61fc40
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=77dae542-a37f-4518-b13e-ef7abc61fc40 ro single
initrd /boot/initrd.img-2.6.27-7-generic

```

These lines are unnecessary now (they are left overs from the kernel you no longer use). You can safely removed them.

Furthermore here:

```

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

```

If you remove the line:

hiddenmenu

You can easily choose between boot options without pressing escape.

If you remove the line:

timeout 3

Then grub does not boot a partition until you pick. You can also make 3 a bigger number (3 is seconds) so that you have longer to choose.

I would leave all lines beginning with the # symbol - these are comments and have no bearing on grub - however it is useful to leave them.

---

### Post by sunseeker888 on 2009-03-24
> **tchoklat said:**
> Add the following atfer ### END DEBIAN AUTOMAGIC KERNELS LIST
 
title Windows 95/98/NT/2000
root (hd0,1)
makeactive
chainloader +1
 
This will give the option of starting windows from grub ...



I think I have botched it

I added 

title Windows 95/98/NT/2000
root (hd0,1)
makeactive
chainloader +1


to grub and saved. 

rebooted

and the options  windows was in the menu

and when I choose windows menu


i get error 13, Invalid or unsupported executable format?



I have installed Ubuntu on a mini hp -laptop and on my pc too, not problem. I followed the same procedure on this laptop.

---

### Post by tchoklat on 2009-03-24
try "rootnoverify (hd0,1)" instead. I assume you are editing the menu.lst file!

---

### Post by James_Lochhead on 2009-03-24
13 : Invalid or unsupported executable format
    This error is returned if the kernel image being loaded is not recognized as Multiboot or one of the supported native formats (Linux zImage or bzImage, FreeBSD, or NetBSD)

---

### Post by sunseeker888 on 2009-03-24
maybe I can mount the ntfs drive, then copy what I need then re-install vista then ubuntu? :(


I am think that would be the best thing, if I cannot resolve the error 13, not recognisable executable format?


I need to pop out now, will see your advices in 2-3 hours


Thanks again

---

### Post by sunseeker888 on 2009-03-24
> **tchoklat said:**
> try "rootnoverify (hd0,1)" instead. I assume you are editing the menu.lst file!

badboy@skyraker:~$ rootnoverify (hd0,1)
bash: syntax error near unexpected token `hd0,1'

---

### Post by philinux on 2009-03-24
Nah, edit your menu.lst file again.

gksudo gedit /boot/grub/menu.lst

Scrool down to the bottom where the windows lines are. Check it's like this.


title Windows XP/Vista or anything you like
 rootnoverify (hd0,1) 
 makeactive
 chainloader +1

---

### Post by mhgsys on 2009-03-24
I think it's because vista wants to be on the first partition.

in linux, open a terminal and typ
```

sudo nano /boot/grub/menu.lst

```

then scroll down to ### END DEBIAN AUTOMAGIC KERNELS LIST

and add

```

title Windows Vista
map (hd0,0) (hd0,1) 
map (hd0,1) (hd0,0) 
rootnoverify(hd0,1)
chainloader +1

```

hit Ctrl + X to write it.
and reboot

(hit esc if you have a hidden menu,)
you can also change the hidden menu by putting # in front of the line

edit: not sure if it works though, I only used the mapping command to map entire disks, not partitions. 
Anyway: I guess it's worth a try, and in the future it's properly easier to install windows first when using 1 disk,

---

### Post by James_Lochhead on 2009-03-24
> **mhgsys said:**
> I think it's because vista wants to be on the first partition.


Shouldn't be a problem. Although I am 100% Ubuntu these days, I used to have Vista installed to the 4th partition and it worked fine.

---

### Post by mhgsys on 2009-03-24
> **James_Lochhead said:**
> Shouldn't be a problem. Although I am 100% Ubuntu these days, I used to have Vista installed to the 4th partition and it worked fine.

Well then should 
```

title Windows Vista
rootnoverify (hd0,1)
chainloader +1

```
work just fine. 

I didn't try it myself though, I always had windows installed first partition.
even on a secondary disk, 
as I said before, 
I've only used the mapping commands to map entire disks, not partitions.
I'm curious though, 
waiting for him to try it 
lol

---

### Post by bruno9779 on 2009-03-24
Sorry if it is complete rubbish, I have read many threads about how windows doesn't accept being slave at boot, and i thought the only workaround was Wubi.

my apologies

---

### Post by mhgsys on 2009-03-24
> **bruno9779 said:**
> Sorry if it is complete rubbish, I have read many threads about how windows doesn't accept being slave at boot, and i thought the only workaround was Wubi.

my apologies

the only workaround for windows being on a slave disk is to map disks.

---

### Post by sunseeker888 on 2009-03-24
> **mhgsys said:**
> I think it's because vista wants to be on the first partition.

in linux, open a terminal and typ
```

sudo nano /boot/grub/menu.lst

```

then scroll down to ### END DEBIAN AUTOMAGIC KERNELS LIST

and add

```

title Windows Vista
map (hd0,0) (hd0,1) 
map (hd0,1) (hd0,0) 
rootnoverify(hd0,1)
chainloader +1

```

hit Ctrl + X to write it.
and reboot

(hit esc if you have a hidden menu,)
you can also change the hidden menu by putting # in front of the line

edit: not sure if it works though, I only used the mapping command to map entire disks, not partitions. 
Anyway: I guess it's worth a try, and in the future it's properly easier to install windows first when using 1 disk,




Did not work same error 13

---

### Post by sunseeker888 on 2009-03-24
> **philinux said:**
> Nah, edit your menu.lst file again.

gksudo gedit /boot/grub/menu.lst

Scrool down to the bottom where the windows lines are. Check it's like this.


title Windows XP/Vista or anything you like
 rootnoverify (hd0,1) 
 makeactive
 chainloader +1



this did not work too :(


re-install vista and ubuntu? Anyway, I want to resize ubuntu partition, to 170Gb and give vista the rest.

What     would be the appropriate, so this problem does not repeat? Install vista first on the first partition, then ubuntu?

---

### Post by mhgsys on 2009-03-24
ok, for kicks, 
would you try this ?
```

title Windows Vista
map (hd0,0) (hd0,1) 
map (hd0,1) (hd0,0) 
rootnoverify(hd0,0)
chainloader +1

```

anyway.. If you choose to reinstall, then yeah. . install vista first, on the first partition,. then install ubuntu. It will see your vista and put it in grub automatically

edit: 
try this one as well

```

title Windows Vista 2 
map (hd0,0) (hd0,1) 
map (hd0,1) (hd0,0) 
rootnoverify(hd0,1)
chainloader +1
makeactive

```

I guess you know you can put in as many as you like.
:-)

---

### Post by meierfra. on 2009-03-24
Since the OP has two hard drives, Vista might not be on boot drive:
also  the boot files  might be on /dev/sda1. So there are a few more entries one could try.  And since Ubuntu did not automatically detect Vista, there is the fair chance that the boot files are missing.
So to get a better picture of your setup, download the Boot Info Script to your   desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

---

### Post by Roaster on 2009-03-24
> **bruno9779 said:**
> Vista only works if you installed ubuntu through Wubi

Why do people give this type of response when there is absolutely no truth to it? Don't answer if you do not know! JMO

---

### Post by mhgsys on 2009-03-24
@ Roaster come on, the dude already said he's sorry, 


 > **bruno9779 said:**
> Sorry if it is complete rubbish, I have read many threads about how windows doesn't accept being slave at boot, and i thought the only workaround was Wubi.

my apologies

---

### Post by sunseeker888 on 2009-03-24
> **mhgsys said:**
> ok, for kicks, 
would you try this ?
```

title Windows Vista
map (hd0,0) (hd0,1) 
map (hd0,1) (hd0,0) 
rootnoverify(hd0,0)
chainloader +1

```

anyway.. If you choose to reinstall, then yeah. . install vista first, on the first partition,. then install ubuntu. It will see your vista and put it in grub automatically

edit: 
try this one as well

```

title Windows Vista 2 
map (hd0,0) (hd0,1) 
map (hd0,1) (hd0,0) 
rootnoverify(hd0,1)
chainloader +1
makeactive

```

I guess you know you can put in as many as you like.
:-)




did not work mate, tried both.

---

### Post by mhgsys on 2009-03-24
I guess you would be helped best by the script of meierfra, I saw him do these kind of wonders before.

---

### Post by sunseeker888 on 2009-03-24
> **meierfra. said:**
> Since the OP has two hard drives, Vista might not be on boot drive:
also  the boot files  might be on /dev/sda1. So there are a few more entries one could try.  And since Ubuntu did not automatically detect Vista, there is the fair chance that the boot files are missing.
So to get a better picture of your setup, download the Boot Info Script to your   desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

=```
============================ Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No known boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbd1a0e96

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    21,467,135    21,465,088  27 Hidden HPFS/NTFS
/dev/sda2          21,467,136   392,644,967   371,177,832   7 HPFS/NTFS
/dev/sda3    *    392,660,730   488,392,064    95,731,335  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2199.0 GB, 2199023185920 bytes
255 heads, 63 sectors/track, 267349 cylinders, total 4294967160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System



blkid -c /dev/null: ____________________________________________________________

/dev/sda3: UUID="77dae542-a37f-4518-b13e-ef7abc61fc40" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sda3 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/badboy/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=badboy)


=========================== sda3/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=77dae542-a37f-4518-b13e-ef7abc61fc40 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=77dae542-a37f-4518-b13e-ef7abc61fc40

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
uuid		77dae542-a37f-4518-b13e-ef7abc61fc40
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=77dae542-a37f-4518-b13e-ef7abc61fc40 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		77dae542-a37f-4518-b13e-ef7abc61fc40
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=77dae542-a37f-4518-b13e-ef7abc61fc40 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		77dae542-a37f-4518-b13e-ef7abc61fc40
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=77dae542-a37f-4518-b13e-ef7abc61fc40 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		77dae542-a37f-4518-b13e-ef7abc61fc40
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=77dae542-a37f-4518-b13e-ef7abc61fc40 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		77dae542-a37f-4518-b13e-ef7abc61fc40
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
title Windows Vista
map (hd0,0) (hd0,1) 
map (hd0,1) (hd0,0) 
rootnoverify(hd0,1)
chainloader +1
makeactive

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=77dae542-a37f-4518-b13e-ef7abc61fc40 /               ext3    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


 247.6GB: boot/grub/menu.lst
 247.6GB: boot/grub/stage2
 247.6GB: boot/initrd.img-2.6.27-11-generic
 247.6GB: boot/initrd.img-2.6.27-7-generic
 247.6GB: boot/vmlinuz-2.6.27-11-generic
 247.6GB: boot/vmlinuz-2.6.27-7-generic
 247.6GB: initrd.img
 247.6GB: initrd.img.old
 247.6GB: vmlinuz
 247.6GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdb

00000000  45 52 02 00 ff ff ff 78  00 00 00 00 00 00 00 00  |ER.....x........|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000030  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000060  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000070  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000090  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000100  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000110  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000120  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000130  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sda1

00000000  67 16 85 b5 04 ac 66 a3  c9 ee c2 7a a1 aa 97 93  |g.....f....z....|
00000010  cb 55 43 b2 65 79 22 bb  fc 34 db 9c e3 c2 65 94  |.UC.ey"..4....e.|
00000020  2a 30 01 e8 40 db 51 47  3d 48 7b c9 30 b1 42 5e  |*0..@.QG=H{.0.B^|
00000030  7c bd 2e 7d b0 61 ce 28  a4 fc cc 3b b6 b7 25 0a  ||..}.a.(...;..%.|
00000040  19 38 79 e3 98 29 b3 37  5c fd 14 28 d5 06 27 e7  |.8y..).7\..(..'.|
00000050  ac d2 37 d2 e8 2e e7 33  6e 95 10 57 df 22 2e c2  |..7....3n..W."..|
00000060  c2 78 21 1a 4f d4 c8 87  09 c5 cc 22 26 99 3e 0a  |.x!.O......"&.>.|
00000070  5e a8 10 86 58 a2 7b 5d  4d 61 73 a5 af b3 b8 b7  |^...X.{]Mas.....|
00000080  7b 97 ac b8 bc 5f 7a ed  24 8d 62 cb d6 4a 6e 9a  |{...._z.$.b..Jn.|
00000090  1b 76 40 43 0b 66 f3 82  39 6d e9 1a 9a 46 7b 70  |.v@C.f..9m...F{p|
000000a0  41 7b 1f b2 e6 9f 25 99  c7 5b 16 12 d4 05 42 2f  |A{....%..[....B/|
000000b0  0a 99 cb e6 cf 77 73 33  24 c0 9a d8 c5 33 cc 7a  |.....ws3$....3.z|
000000c0  b5 27 a0 db f2 4b c3 8a  31 58 61 7d 31 cf 34 cf  |.'...K..1Xa}1.4.|
000000d0  9d db 85 17 c9 44 49 7a  b5 81 ae cb 36 f1 be c8  |.....DIz....6...|
000000e0  44 d7 cc ca 97 ac 57 29  a8 f7 43 61 2e 53 d1 bb  |D.....W)..Ca.S..|
000000f0  34 e3 70 39 83 58 71 a0  7c 7c 12 cb 2b 3c a4 d3  |4.p9.Xq.||..+<..|
00000100  8d 1a 94 ba cb f5 17 fe  db b8 17 36 3b f7 6e e4  |...........6;.n.|
00000110  42 fb b0 4e 55 10 5f 8b  74 ca 39 20 f4 64 16 df  |B..NU._.t.9 .d..|
00000120  38 1c 33 77 dc 33 ba a9  15 15 fb a1 39 98 42 18  |8.3w.3......9.B.|
00000130  ed ae 35 98 61 59 b9 b4  b5 f8 21 72 27 07 e6 d7  |..5.aY....!r'...|
00000140  d1 7a 7f b6 72 3d 71 fb  df 5c 2d bb 9e e7 30 cf  |.z..r=q..\-...0.|
00000150  60 48 59 1c 9c e7 46 b8  50 34 b2 83 a4 e3 44 6d  |`HY...F.P4....Dm|
00000160  b6 91 b3 4a 2f 6e 42 25  03 a8 25 88 24 92 61 d9  |...J/nB%..%.$.a.|
00000170  14 de 80 c4 e9 e7 0d 70  05 b9 c5 b3 a8 28 9b 54  |.......p.....(.T|
00000180  6e 5f 9b 8c f7 25 fe 85  0c 01 a9 e0 dc 23 7c 2d  |n_...%.......#|-|
00000190  5e 54 5a b7 76 09 23 37  75 a2 5a 65 90 d9 4f 73  |^TZ.v.#7u.Ze..Os|
000001a0  f7 00 9d 59 73 9b 6d bc  5b 3a ef 98 4e 37 44 a3  |...Ys.m.[:..N7D.|
000001b0  16 1f 9f 1f 48 db 2a 33  ab cd bd bf e0 2b 18 c7  |....H.*3.....+..|
000001c0  ad a3 74 f1 46 c3 67 7d  ea 34 85 81 f7 7f b5 ef  |..t.F.g}.4......|
000001d0  50 be d9 23 f0 6d b7 e6  5f 0b fa 8d b9 b4 1b fe  |P..#.m.._.......|
000001e0  3d 19 fe cf ed 04 db 73  f2 f5 4f f2 c8 b4 4d 22  |=......s..O...M"|
000001f0  89 f1 ce 09 0a a7 44 74  f2 36 de 2e 29 af 22 45  |......Dt.6..)."E|
00000200

Unknown BootLoader  on sda2

00000000  3e 8d 8e 09 46 c6 69 2b  7b 5e 31 5b 76 3a 48 9b  |>...F.i+{^1[v:H.|
00000010  7b 83 69 a2 b8 94 70 6c  6b 03 87 32 d4 b4 5b 16  |{.i...plk..2..[.|
00000020  8a f1 b2 a7 7e 34 d4 c4  f7 eb c6 2b 4d b4 1a a0  |....~4.....+M...|
00000030  d4 d0 4f d0 57 db 98 bd  6e b1 94 c9 f6 40 e5 a7  |..O.W...n....@..|
00000040  5c 18 d0 d4 0f 5f b2 60  8f 0b d1 e9 97 6d ba ea  |\...._.`.....m..|
00000050  f7 cd b0 2a 39 36 19 aa  e8 b4 eb 22 0c 9f 11 d8  |...*96....."....|
00000060  0b 41 6f 16 4d 56 2a b6  03 c8 cc 4f 01 f5 20 9b  |.Ao.MV*....O.. .|
00000070  f0 e5 a9 ce 79 fb f6 18  61 01 c8 41 6a 9e cb 8b  |....y...a..Aj...|
00000080  87 90 40 92 35 8e d4 0d  c4 e3 72 52 f4 6f 38 8a  |..@.5.....rR.o8.|
00000090  ce 34 5f b8 44 83 3b 02  89 07 31 02 b8 5d 57 54  |.4_.D.;...1..]WT|
000000a0  92 b5 d5 7c 5e c5 32 59  93 4a 29 8c a6 78 be fb  |...|^.2Y.J)..x..|
000000b0  5c de f6 5c 5f 6a 1f 29  fd d1 c9 ec 6b ad 31 3e  |\..\_j.)....k.1>|
000000c0  bd 4c 7f 54 a7 6e d2 72  3b b6 59 5a 58 be db 0b  |.L.T.n.r;.YZX...|
000000d0  9d ef 34 7a 32 4c 8a c6  74 0e 71 e6 8d 2d 62 cd  |..4z2L..t.q..-b.|
000000e0  31 5f 7e 2e f9 20 b0 8b  34 df 86 d8 d2 48 0e c7  |1_~.. ..4....H..|
000000f0  da a1 60 ea eb b8 e7 c3  a0 34 0a 44 9d 86 c5 98  |..`......4.D....|
00000100  a3 1a 20 4a 16 74 18 b7  08 3f f2 c1 14 78 7a 2b  |.. J.t...?...xz+|
00000110  15 ec 32 0f 9b 88 0e 56  2f 6f 61 b7 c1 5c b7 7a  |..2....V/oa..\.z|
00000120  43 ad 36 99 fc 37 37 b6  f3 90 ca bd 33 9a a8 0c  |C.6..77.....3...|
00000130  18 a5 07 76 6b ae ed 2b  a0 60 02 cc 1c 28 5f 61  |...vk..+.`...(_a|
00000140  bb 89 e2 0c d3 ae 2a d0  bb 02 b3 c2 23 6c e0 4a  |......*.....#l.J|
00000150  22 7e 41 65 c1 19 43 4d  3b ce 7e 00 85 81 98 ca  |"~Ae..CM;.~.....|
00000160  58 d1 b8 17 22 a4 a7 68  0e d6 57 ce 7b a2 ce 6c  |X..."..h..W.{..l|
00000170  b6 d4 ce ad 7f 67 ce ed  6e 5b 30 44 cc c6 1f 14  |.....g..n[0D....|
00000180  c4 e6 3e c7 01 c4 85 12  24 79 e7 1e 48 46 91 ea  |..>.....$y..HF..|
00000190  74 4c fc 46 ae 85 ef 5a  56 09 76 c1 9e 7a aa d1  |tL.F...ZV.v..z..|
000001a0  dc fd 50 f2 27 5e 58 55  ec b7 77 a1 34 61 68 6d  |..P.'^XU..w.4ahm|
000001b0  6a 9b 25 70 0c df 5e b7  63 69 4a c8 21 54 d8 b6  |j.%p..^.ciJ.!T..|
000001c0  3f d8 27 53 33 5e 51 70  38 31 48 11 12 99 00 6b  |?.'S3^Qp81H....k|
000001d0  db 89 1c e2 62 c5 06 ac  ca 7f 0e 7c 63 20 ae 5d  |....b......|c .]|
000001e0  81 5a 0c 62 88 76 37 25  6e 0f 3a 84 41 f4 55 8b  |.Z.b.v7%n.:.A.U.|
000001f0  23 a6 28 19 60 c7 3e f3  0a 2d c7 1a 84 90 99 80  |#.(.`.>..-......|
00000200


```

---

### Post by lisati on 2009-03-24
> **bruno9779 said:**
> Vista only works if you installed ubuntu through Wubi

I, too, have a dual-boot installation with Vista that doesn't use Wubi. It can be done! 

Keep up the good work, team!

---

### Post by meierfra. on 2009-03-24
The boot sectors of the Vista partition and of /dev/sda1 are corrupted.  I don't remember seeing I case like this and I have  no idea how this could have happened.  Did you get any error messages while installing ubuntu? Do you have any idea what might have caused this?

Fixing the boot sector of your Vista partition is fairly easy. But I don't know whether the damage is restricted to the boot sector. So you should also run a file system check:


Boot from you Vista CD (if you don't have one you can get a Vista Repair CD from [here]("http://www.pcworld.com/downloads/file/fid,71039/description.html")

At the first screen select you favorite language.
At the second screen, select "Install Now"
At the third screen, press "Shift F10".

This will open a terminal. Type 

```
bootrec /fixboot
```

That should fix your boot sector.  If you get some error messages, let me know and I can show you how to fix the boot sector from Ubuntu.

Next type 

```
diskpart 
```

and at the "diskpart>" prompt

```
 list volume
```

This will list the drive letters for all the 'NTFS' and 'Fat' partitions on your computer. Determine the drive letter for your Vista partition
(But since the Vista partition is corrupted there is some chance that your Vista partition is not listed)


Type

```
exit
```

and 

then

```
chkdsk /r C:
```

(Here replace "C:" by the drive letter of your Vista partition. If "list volume"  did not list your "Vista" partition, just  use "chkdsk /r" without a drive letter.

Run "chkdsk /r C:" as often as it takes (until it does not find anymore ).

---

### Post by sunseeker888 on 2009-03-24
> **meierfra. said:**
> The boot sectors of the Vista partition and of /dev/sda1 are corrupted.  I don't remember seeing I case like this and I have  no idea how this could have happened.  Did you get any error messages while installing ubuntu? Do you have any idea what might have caused this?

Fixing the boot sector of your Vista partition is fairly easy. But I don't know whether the damage is restricted to the boot sector. So you should also run a file system check:


Boot from you Vista CD (if you don't have one you can get a Vista Repair CD from [here]("http://www.pcworld.com/downloads/file/fid,71039/description.html")

At the first screen select you favorite language.
At the second screen, select "Install Now"
At the third screen, press "Shift F10".

This will open a terminal. Type 

```
bootrec /fixboot
```

That should fix your boot sector.  If you get some error messages, let me know and I can show you how to fix the boot sector from Ubuntu.

Next type 

```
diskpart 
```

and at the "diskpart>" prompt

```
 list volume
```

This will list the drive letters for all the 'NTFS' and 'Fat' partitions on your computer. Determine the drive letter for your Vista partition
(But since the Vista partition is corrupted there is some chance that your Vista partition is not listed)


Type

```
exit
```

and 

then

```
chkdsk /r C:
```

(Here replace "C:" by the drive letter of your Vista partition. If "list volume"  did not list your "Vista" partition, just  use "chkdsk /r" without a drive letter.

Run "chkdsk /r C:" as often as it takes (until it does not find anymore ).



thanks I will try those steps now. there were no errors when I installed ubuntu, but it did not see vista though, or import anything, I thought it coud be just grub when I rebooted

I update this tomorrow give you guys the results

cheers

---

### Post by sunseeker888 on 2009-03-24
Code:

bootrec /fixboot

That should fix your boot sector. If you get some error messages, let me know and I can show you how to fix the boot sector from Ubuntu.


no there error it didnot get recognised or not to use corruptted disk

---

### Post by meierfra. on 2009-03-24
I was worried about that. 

There is some change that it isn't the boot sector which is corrupt, but the partition table. So I suggest to have a look at your partitions with testdisk:


download the [testdisk-6.10.linux26.tar.bz2 package](http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2) to your desktop, and then do:

```


cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static  /dev/sda

```

After starting testdisk with the above command, choose 
 "Proceed",
 "Intel",
 "Analyze",
 "Quick search",
Press "Y"  (to search for Vista partitions)
Press  "Enter" to continue, 
select "Deeper Search" (so it does a deeper search, which could take a while) 

Please post the output of the screen that has the deep search results. Also, use your up/down arrow keys to select each partition listed in the deep search results, and press "p" to get a directory listing; please let me know exactly which partitions give you a directory listing.

---

### Post by sunseeker888 on 2009-03-25
> **meierfra. said:**
> I was worried about that. 

There is some change that it isn't the boot sector which is corrupt, but the partition table. So I suggest to have a look at your partitions with testdisk:


download the [testdisk-6.10.linux26.tar.bz2 package](http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2) to your desktop, and then do:

```


cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static  /dev/sda

```

After starting testdisk with the above command, choose 
 "Proceed",
 "Intel",
 "Analyze",
 "Quick search",
Press "Y"  (to search for Vista partitions)
Press  "Enter" to continue, 
select "Deeper Search" (so it does a deeper search, which could take a while) 

Please post the output of the screen that has the deep search results. Also, use your up/down arrow keys to select each partition listed in the deep search results, and press "p" to get a directory listing; please let me know exactly which partitions give you a directory listing.


Hello

Thanks for posts.

I run the test 4 time, one full test on sda
then each partition on each own, there's definitely problem




Running test disk, got the following, it's saying invalid NTFS boot, and no option to choose vista partition, and quick search, it searched on the Linux one. I have tried running a few times, but still no option to test the NTFS


TestDisk 6.10, Data Recovery Utility, July 2008

Christophe GRENIER <grenier@cgsecurity.org>

[http://www.cgsecurity.org](http://www.cgsecurity.org)



Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63

Current partition structure:

     Partition                  Start        End    Size in sectors



 1 P Windows RE(store)        0  32 33  1336  68 12   21465088

Invalid NTFS boot

 2 P HPFS - NTFS           1336  68 13 24441   4 51  371177832

 2 P HPFS - NTFS           1336  68 13 24441   4 51  371177832

 3 * Linux                24442   0  1 30400 254 63   95731335









*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted

[Quick Search]  [ Backup ]

                            Try to locate partition



Only one partition found


Disk /dev/sda - 250 GB / 232 GiB - CHS 30402 255 63

     Partition               Start        End    Size in sectors

* Linux                24442   0  1 30400 254 63   95731335














Structure: Ok.  Use Up/Down Arrow keys to select partition.


Use Left/Right Arrow keys to CHANGE partition characteristics:

*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted

Keys A: add partition, L: load backup, T: change type, P: list files,

     Enter: to continue

EXT3 Large file Sparse superblock Recover, 49 GB / 45 GiB





Then I change the command to this sudo testdisk-6.10/linux/testdisk_static /dev/sda
2

got this message
[B]&#8220;Partition sector doesn't have the endmark 0xAA55
&#8221;[/B]

, but I was able to do a quicksearch
Should TestDisk search for partition created under Vista ? [Y/N] (answer Yes if

unsure)


Y

then


result


Disk /dev/sda2 - 190 GB / 176 GiB - CHS 23105 255 63

     Partition               Start        End    Size in sectors



Structure: Ok.



Keys A: add partition, L: load backup, Enter: to continue





I perform the test on 1st & 2nd too separately
  TestDisk is free software, and

comes with ABSOLUTELY NO WARRANTY.



Select a media (use Arrow keys, then press Enter):

Disk /dev/sda1 - 10 GB / 10 GiB - TOSHIBA MK2546GSX                       



Disk /dev/sda1 - 10 GB / 10 GiB - CHS 1336 255 63

Current partition structure:

     Partition                  Start        End    Size in sectors





Partition sector doesn't have the endmark 0xAA55




result
Disk /dev/sda1 - 10 GB / 10 GiB - CHS 1337 255 63

     Partition               Start        End    Size in sectors



Structure: Ok.



  TestDisk is free software, and

comes with ABSOLUTELY NO WARRANTY.



Select a media (use Arrow keys, then press Enter):

Disk /dev/sda3 - 49 GB / 45 GiB - TOSHIBA MK2546GSX                       



Partition sector doesn't have the endmark 0xAA55



Disk /dev/sda3 - 49 GB / 45 GiB - CHS 5959 255 63



The harddisk (49 GB / 45 GiB) seems too small! (< 73 GB / 68 GiB)

Check the harddisk size: HD jumpers settings, BIOS detection...



The following partitions can't be recovered:

     Partition               Start        End    Size in sectors

  Linux                 2957  19  7  8916  18 62   95731328

  Linux                 2959  29 15  8918  29  7   95731328

  Linux                 2960  66 51  8919  66 43   95731328

  Linux                 2961  71 55  8920  71 47   95731328

  Linux                 2961 169 25  8920 169 17   95731328

  Linux                 2962 109 28  8921 109 20   95731328

  Linux                 2963  49 31  8922  49 23   95731328

  Linux                 2964 249 38  8923 249 30   95731328

  Linux                 2965 124 40  8924 124 32   95731328



continue
Disk /dev/sda3 - 49 GB / 45 GiB - CHS 5959 255 63

     Partition               Start        End    Size in sectors




Structure: Ok.

---

### Post by sunseeker888 on 2009-03-25
If i have to kill the disk with Gparted, and resize the partition, as vista will get only 30GB on this laptop, what's the best way. Re-installed vista first on the 1st partition, then ubuntu on the 2nd one.

sda1 is the recovery partition which I am not touching.

will it matter if vista goes sda2? 


I have followed the installation process properly on 2 other units last week, and they both work perfectly, have the grub dual boot. I am leaving windows for good now, as I can perform my work on web based application finally, bye bye windows vista ultimate 64 bits (what a garbage, bsod every day). The only reasons, I could not move before was of my work stuffs. I have codeweavers now, for essential things I need to run.


Last you could possibly tell me

I am using 64 bits ubuntu now, my plugins for firefox are not workin as some are 32 bits.
 
could you please tell the command to uninstal firefox , and the command afterwards to install firefix 32 bits, so I can use my plugins. I am still a dummy in the commands

Thanks everyong for all your efforts, it's ok I will just kill the disk if it cannot repair, and resize it properly. This laptop is new, and do want backups anyway.

---

### Post by meierfra. on 2009-03-25
Just a couple of comments on  your testdisk results. 

1)  One cannot run testdisk on  partition, so the results from those test have no meaning

2)  When you run testdisk on /dev/sda you did not to the "Deep Search".   
The Quick Search also is not very meaning full.

 So I suggested to run testdisk again, this time follow the instruction from my previous post exactly.

> sda1 is the recovery partition which I am not touching.
You recovery partition seems just as damaged as the Vista partition. So unless the testdisk "Deep Search" comes up with some positive results, I suggest to delete the recovery partition as well.


Since you are planning to resize the Ubuntu partition and since its a fresh install I recommend to also deleted the Ubuntu partition. Reinstalling is  much faster than resizing and any resizing  has a small risk of causing damage.

So  I would delete all the partition. Also I recommend to create a Home or Data partition. Personally, I prefer a Data partition, but a Home partition seems to be more popular.

So I would partition your drive as  follows

sda1:  ntfs 30GB  (for Vista)
sda2:  ext3 20GB  (Ubuntu "/")
sda3   extended 200GB
sda5   ext3     200-size of swap  (Data)
sda6   swap      equal to the amount of your ram, but at least 2GB


You might also consider creating another "ntfs" partition for sharing Data between Vista and Ubuntu


> I am using 64 bits ubuntu now, my plugins for firefox are not workin as some are 32 bits.
Sorry I don't know anything about this. So search the forum or start a new thread

---

### Post by carl_pr on 2009-03-25
> **bruno9779 said:**
> Vista only works if you installed ubuntu through Wubi

i have vista and ubuntu and works fine.

---

### Post by heatblazer on 2009-03-25
> **bruno9779 said:**
> Vista only works if you installed ubuntu through Wubi

I have a dual boot Ubuntu/Vista with normal install. I re-installed vista then intalled GRUB again. I did that on ubuntu 7.04, but I guess it will work with 8.04 too.

---

### Post by sunseeker888 on 2009-03-25
> **meierfra. said:**
> Just a couple of comments on  your testdisk results. 

1)  One cannot run testdisk on  partition, so the results from those test have no meaning

2)  When you run testdisk on /dev/sda you did not to the "Deep Search".   
The Quick Search also is not very meaning full.

 So I suggested to run testdisk again, this time follow the instruction from my previous post exactly.


You recovery partition seems just as damaged as the Vista partition. So unless the testdisk "Deep Search" comes up with some positive results, I suggest to delete the recovery partition as well.


Since you are planning to resize the Ubuntu partition and since its a fresh install I recommend to also deleted the Ubuntu partition. Reinstalling is  much faster than resizing and any resizing  has a small risk of causing damage.

So  I would delete all the partition. Also I recommend to create a Home or Data partition. Personally, I prefer a Data partition, but a Home partition seems to be more popular.

So I would partition your drive as  follows

sda1:  ntfs 30GB  (for Vista)
sda2:  ext3 20GB  (Ubuntu "/")
sda3   extended 200GB
sda5   ext3     200-size of swap  (Data)
sda6   swap      equal to the amount of your ram, but at least 2GB


You might also consider creating another "ntfs" partition for sharing Data between Vista and Ubuntu



Sorry I don't know anything about this. So search the forum or start a new thread




thank you so much. This was the output from deep search. I do not know why nothing else came.

Even in gparted now, it cannot see the NTFS partition. Could it be a hard disk failure or some shock? as I can not see why 2 partitions gor corrupted, this laptop is brand new.


Anyway, I am going ahead now of the resize the drive, and using the above format you gave me, I check the hdd integrity also


Thank you again for your time


Cheers

S888

---

### Post by meierfra. on 2009-03-25
> I check the hdd integrity also

Good idea.
Good luck.

---

### Post by mhgsys on 2009-03-25
good luck, 

remember to install xp / vista first. 

makes it a little bit easier from the start.
:lolflag:

---

### Post by sunseeker888 on 2009-03-26
Guys

it's done

re-installed everything, vista first and then ubuntu. My sony recovery disk unfortunately would not let me create a vista partition below 50GB. 


I have my suspicion now, why things botched up. I did use the alternate disk of intrepid so I could use the encryption, could this has caused all the partition problems? It specifically say it has to be on master not slave? I am not savvy in Linux yet, could this be the problem.

---

### Post by meierfra. on 2009-03-26
> it's done

Great. Have fun with Vista and Ubuntu.

> the encryption,

I don't know anything about encryption. But at least this whole thing make some sense now: sda1 and sda2 got encrypted.  Your really should have mentioned the encryption in your very first post. Maybe then somebody who knows something about encryption could have helped you.

---

