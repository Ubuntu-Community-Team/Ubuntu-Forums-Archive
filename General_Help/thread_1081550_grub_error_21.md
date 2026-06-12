---
title: "grub error 21"
date: 2009-02-26
forum: General Help
---

### Post by bobmatino17 on 2009-02-26
one day i had this idea to have a full install of ubuntu on my flash drive (formatted w/ ext2) not using UNetBootin. all went well with the install, except a day later, a tried to boot my computer and i got a grub error 21. So i had the idea to use a deb cd to rescue it, but it couldnt understand my computers ext4 partition. anyone know how to fix this?

---

### Post by dbbolton on 2009-02-26
> **bobmatino17 said:**
> one day i had this idea to have a full install of ubuntu on my flash drive (formatted w/ ext2) not using UNetBootin. all went well with the install, except a day later, a tried to boot my computer and i got a grub error 21. So i had the idea to use a deb cd to rescue it, but it couldnt understand my computers ext4 partition. anyone know how to fix this?
Which version of Debian was it?

You might have to look for a Live CD with ext4-utils. I think the latest version of GParted has it.

---

### Post by bobmatino17 on 2009-02-26
> Which version of Debian was it?

You might have to look for a Live CD with ext4-utils. I think the latest version of GParted has it.

its version 4.0

---

### Post by thtrgremlin on 2009-02-26
I don't know this problem specifically, but: if you boot from a live CD, go to a terminal, mount your hard drive partition you want rescued, 'cd' to the root of that system and ```
sudo chroot /dev/<disk> /bin/bash
```You are now using your computers tools as far as the command line is concerned. Then just update/upgrade ```
sudo apt-get update
sudo apt-get dist-upgrade
```If this was a but you got from an update, and it has been fixed already.

I have used alpha/beta releases in the past and have had this problem. The problem with patching in these cases is how to patch a system that won't boot anymore. This is it.

However, if they fixed this problem, but if for whatever reason 'update-grub' was not invoked, do that manually. Also, if just for curiosity sake, look and see if there is a difference between /boot/grub/menu.lst and /boot/grub/menu.lst~ to see what changed, keeping in mind the 'modified date', menu.lst~ might be older than your problem.

Hope this helps.

And in case it needs to be said, this is a good reason not to use alpha/beta releases. I know the temptation, and they usually work so flawlessly anyway.

---

### Post by thtrgremlin on 2009-02-26
ooh, rereading your question, I personally have had the experience that a live CD of whatever system you have installed makes the best rescue disk, in case that needed to be clarified.

I hate that when I use "reply to thread", I can't see the question any more, and can get off topic without realizing it, but anyway  :)

---

### Post by caljohnsmith on 2009-02-26
I think either of these threads will most likely have the solution to your problem:

[http://ubuntuforums.org/showthread.php?p=6665548](http://ubuntuforums.org/showthread.php?p=6665548)
[http://ubuntuforums.org/showthread.php?p=6452340](http://ubuntuforums.org/showthread.php?p=6452340)

Let me know how that goes or if you run into problems.

---

### Post by bobmatino17 on 2009-02-26
I tried running the command...
```
grub> find /boot/grub/stage1
```
and i got...
```
Error 15: File not found
```
so since i know the partition is (hd0,0) i tried...
```
grub> root (hd0,0)

```
and got...
```
Error 12: Invalid device requested
```
any help would be enjoyed.

---

### Post by caljohnsmith on 2009-02-26
Did you run Grub as root user, i.e. with sudo?
```
[COLOR="Blue"]sudo[/COLOR] grub
```

EDIT: So are you trying to do this with Jaunty I assume? If so, are you using the Jaunty Live CD? It would be important to run the Grub commands using whichever version of Grub Jaunty uses, because previous Ubuntu releases obviously don't support ext4.

---

### Post by bobmatino17 on 2009-02-26
> **caljohnsmith said:**
> Did you run Grub as root user, i.e. with sudo?
```
[COLOR="Blue"]sudo[/COLOR] grub
```

EDIT: So are you trying to do this with Jaunty I assume? If so, are you using the Jaunty Live CD? It would be important to run the Grub commands using whichever version of Grub Jaunty uses, because previous Ubuntu releases obviously don't support ext4.
i was running as root and im still using a cd. wish i was using an hd though :(

---

### Post by caljohnsmith on 2009-02-26
So which Live CD are you using? I think it would help to get more info about your setup, so how about downloading the **Boot Info Script** to your Ubuntu Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post.

---

### Post by bobmatino17 on 2009-02-26
I attached the RESULTS.txt file for you. or i didnt...

---

### Post by bobmatino17 on 2009-02-26
well here is the output....

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu jaunty (development 
                       branch)
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0741425b

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   195,318,269   195,318,207  83 Linux
/dev/sda2         195,318,270   199,222,064     3,903,795   5 Extended
/dev/sda5         195,318,333   199,222,064     3,903,732  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="4759b464-2d7c-4392-b67b-332f84356b5c" TYPE="ext4" 
/dev/sda5: UUID="42e73ac1-3784-405e-b844-c0feb1cf811e" TYPE="swap" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-6-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-6-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /media/disk type ext4 (rw,nosuid,nodev,uhelper=hal)


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
# kopt=root=UUID=4759b464-2d7c-4392-b67b-332f84356b5c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=4759b464-2d7c-4392-b67b-332f84356b5c

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

title		Ubuntu jaunty (development branch), kernel 2.6.28-6-generic
uuid		4759b464-2d7c-4392-b67b-332f84356b5c
kernel		/boot/vmlinuz-2.6.28-6-generic root=UUID=4759b464-2d7c-4392-b67b-332f84356b5c ro quiet splash 
initrd		/boot/initrd.img-2.6.28-6-generic
quiet

title		Ubuntu jaunty (development branch), kernel 2.6.28-6-generic (recovery mode)
uuid		4759b464-2d7c-4392-b67b-332f84356b5c
kernel		/boot/vmlinuz-2.6.28-6-generic root=UUID=4759b464-2d7c-4392-b67b-332f84356b5c ro  single
initrd		/boot/initrd.img-2.6.28-6-generic

title		Ubuntu jaunty (development branch), memtest86+
uuid		4759b464-2d7c-4392-b67b-332f84356b5c
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=4759b464-2d7c-4392-b67b-332f84356b5c /               ext4    relatime,errors=remount-ro 0       1
# none was on /dev/sda5 during installation
UUID=42e73ac1-3784-405e-b844-c0feb1cf811e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .6GB: boot/grub/menu.lst
   1.7GB: boot/grub/stage2
  15.4GB: boot/initrd.img-2.6.28-6-generic
   1.9GB: boot/vmlinuz-2.6.28-6-generic
  15.4GB: initrd.img
   1.9GB: vmlinuz
```

---

### Post by caljohnsmith on 2009-02-26
This is the third time I've asked you, but which Live CD are you using?

---

### Post by bobmatino17 on 2009-02-26
sry, 9.04 alpha (downloaded from latest link at distrowatch at time)

---

### Post by caljohnsmith on 2009-02-26
OK, how about posting the output of:
```
apt-cache policy grub
```
Next try:
```
sudo mount /dev/sda1 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo chroot /mnt
grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
exit

```
If any of the above commands return an error, please copy your entire terminal session with all the commands to your next post so I can see exactly what happened. If they complete successfully though, go ahead and reboot, and let me know exactly what happens when you boot the HDD.

---

### Post by bobmatino17 on 2009-02-26
```
ubuntu@ubuntu:~$ apt-cache policy grub
grub:
  Installed: 0.97-29ubuntu48
  Candidate: 0.97-29ubuntu48
  Version table:
 *** 0.97-29ubuntu48 0
        500 http://archive.ubuntu.com jaunty/main Packages
        100 /var/lib/dpkg/status
ubuntu@ubuntu:~$ 

```

all of the commands returned ok.

---

### Post by bobmatino17 on 2009-02-26
ty very,very,very,very much, my computer now boots without the cd!

---

### Post by caljohnsmith on 2009-02-26
Glad to hear that worked OK; cheers and have fun with your Jaunty Ubuntu install.

---

### Post by terencezumhb7 on 2011-01-16
> **bobmatino17 said:**
> I attached the RESULTS.txt file for you. or i [[COLOR=#000000]didnt[/COLOR]](http://www.purplers.net/zh-cn/sports/randy-couture-is-a-complex-fighter.html)...I encountered the same problem, It annoys me long, Your effort is appreciated! Finally got the workaround.

---

