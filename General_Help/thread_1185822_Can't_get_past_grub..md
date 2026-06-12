---
title: "Can't get past grub."
date: 2009-06-12
forum: General Help
---

### Post by mlsquad on 2009-06-12
I edited menu.lst to add an option to boot into Windows and then rebooted.  Now it doesn't even ask me which OS to boot, it just goes straight to a grub terminal.  I backed out my modifications by booting to a live CD, but I still just boot into grub.  I even reinstalled grub from the live CD, but to no avail.  This is on Ubuntu 9.04 Jaunty.  Any ideas on how to get my grub functioning again?

---

### Post by synapsys on 2009-06-12
How exactly did you re-install grub from live cd? Do you have more than one hard drive? Did you install to correct hard drive? Please list exact commands you used from live cd.

---

### Post by mlsquad on 2009-06-12
> **synapsys said:**
> How exactly did you re-install grub from live cd? Do you have more than one hard drive? Did you install to correct hard drive? Please list exact commands you used from live cd.

sudo grub
root (hd0,0)
setup (hd0)
quit

I am 100% sure that hd0,0 is the correct location of the filesystem.

---

### Post by synapsys on 2009-06-12
What happens if you enter 'boot' from grub prompt? Does it give error message? If you enter:

```
find /boot/grub/stage1
```

From grub prompt does it return hd0,0 like it's supposed to?

---

### Post by mlsquad on 2009-06-13
> **synapsys said:**
> What happens if you enter 'boot' from grub prompt? Does it give error message?```
Starting up ...

Error 8: Kernel must be loaded before booting

``` > **synapsys said:**
> If you enter:

```
find /boot/grub/stage1
```

From grub prompt does it return hd0,0 like it's supposed to?

Indeed, it does return hd(0,0)

---

### Post by synapsys on 2009-06-13
It appears your /boot/grub/menu.lst is screwed up, as grub can't find your kernel. Please boot to livecd and post contents of /boot/grub/menu.lst so we can figure out what went wrong. Reinstalling grub only installs it to the boot sector of the disk, your boot menu remains untouched.

---

### Post by mlsquad on 2009-06-13
> **synapsys said:**
> It appears your /boot/grub/menu.lst is screwed up, as grub can't find your kernel. Please boot to livecd and post contents of /boot/grub/menu.lst so we can figure out what went wrong. Reinstalling grub only installs it to the boot sector of the disk, your boot menu remains untouched.
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
timeout 10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
# hiddenmenu

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
# kopt=root=UUID=42212fb3-429f-43be-b711-97bda3a041ff ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=42212fb3-429f-43be-b711-97bda3a041ff

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		42212fb3-429f-43be-b711-97bda3a041ff
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=42212fb3-429f-43be-b711-97bda3a041ff ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		42212fb3-429f-43be-b711-97bda3a041ff
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=42212fb3-429f-43be-b711-97bda3a041ff ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		42212fb3-429f-43be-b711-97bda3a041ff
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```Some more relevant information:
```
ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="42212fb3-429f-43be-b711-97bda3a041ff" TYPE="ext4" 
/dev/sda2: UUID="1C0A0BEF0A0BC52C" LABEL="System Reserved" TYPE="ntfs" 
/dev/sda3: UUID="B46811DF6811A0E2" TYPE="ntfs" 
/dev/sda5: UUID="a3b04d1e-89a5-4396-9404-b2c45796b427" TYPE="swap" 
/dev/sdb1: UUID="d7b3b980-369a-4bb9-8671-1dffeecef71b" TYPE="ext4" 
ubuntu@ubuntu:~$ cd /media/disk/boot/
ubuntu@ubuntu:/media/disk/boot$ ls
abi-2.6.28-11-generic         memtest86+.bin
config-2.6.28-11-generic      System.map-2.6.28-11-generic
grub                          vmcoreinfo-2.6.28-11-generic
initrd.img-2.6.28-11-generic  vmlinuz-2.6.28-11-generic

```

---

### Post by synapsys on 2009-06-13
Man.... everything looks kosher pickles but just for ducks try running:

```
sudo update-grub
```

Just in case.

---

### Post by mlsquad on 2009-06-13
```
ubuntu@ubuntu:~$ sudo update-grub 
Searching for GRUB installation directory ... 
No GRUB directory found. To create a template run 'mkdir /boot/grub' first. To install grub, install it manually or try the 'grub-install' command. ### Warning, grub-install is used to change your MBR. ###

```

---

### Post by merlinus on 2009-06-13
What is on sdb1?  Also, did you run those commands whilst booted into ubuntu, or using the live cd?

---

### Post by mlsquad on 2009-06-13
> **merlinus said:**
> What is on sdb1?  Also, did you run those commands whilst booted into ubuntu, or using the live cd?

sdb1 is my home directory.  I can't boot into Ubuntu to do anything.  I can only boot into the live CD.

---

### Post by synapsys on 2009-06-13
Maybe the livecd is trying to run it's own version of update-grub, try running the script in your /sbin/ folder. If that doesn't work try changing 'root' to hd0,0 instead of uuid in your menu.lst.

---

### Post by merlinus on 2009-06-13
If you are running from the live cd, then /boot/grub/menu.lst is NOT the one that exists in your ubuntu install.

You can manually mount your ubuntu partition from a terminal, and get to its menu.lst that way.

---

### Post by synapsys on 2009-06-13
I was assuming he knew that...  sounds like he knows mostly what he's doing.

---

### Post by merlinus on 2009-06-13
No insult intended, but he did post menu.lst, and it appears to be the one from the live cd.....

Of course, I could easily be totally mistaken!

---

### Post by synapsys on 2009-06-13
no answer.... did you fix it?

---

### Post by mlsquad on 2009-07-02
> **synapsys said:**
> no answer.... did you fix it?

Sorry, ubuntuforums didn't e-mail me that there was an update to this post.  My computer went belly up and so this issue has not been of much priority.  My BIOS displays green speckles on the screen, and booting from a live CD gives me a hard freeze when it tries to go into graphics mode, so I'm working on that one.

I did post the menu.lst from my hard drive at /media/.../boot/grub/menu.lst, not the live CD version at /boot/grub/menu.lst  I'll let y'all know when my hardware is back in commission.  Thanks for the help thus far.

---

### Post by mlsquad on 2009-07-07
> **synapsys said:**
> Maybe the livecd is trying to run it's own version of update-grub, try running the script in your /sbin/ folder. If that doesn't work try changing 'root' to hd0,0 instead of uuid in your menu.lst.

I replaced my graphics card and now my computer can boot.  I did run the update-grub from /media/disk/sbin and I am still in the same spot.  I still cannot boot up. :(

---

### Post by mlsquad on 2009-07-07
Here's some more good information.  When I boot up and get the grub menu I can boot by typing in the following.
rootnoverify (hd0,0)
makeactive
chainloader +1
kernel /vmlinuz root=/dev/sda1
boot

So I think it is definitely something crazy with this menu.lst, but I cannot figure out what.  It is owned by root with rw_r__r__ permission.

---

### Post by mlsquad on 2009-09-01
I finally got this fixed!

[http://ubuntuforums.org/showthread.php?t=1104822](http://ubuntuforums.org/showthread.php?t=1104822) led me to [http://wiki.archlinux.org/index.php/Ext4](http://wiki.archlinux.org/index.php/Ext4)

```

mkdir /mnt/arch
mount -t ext4 /dev/sda1 /mnt/arch
mount -t proc proc /mnt/arch/proc
mount -t sysfs sys /mnt/arch/sys
mount -o bind /dev /mnt/arch/dev
chroot /mnt/arch /bin/bash
grub-install --recheck /dev/sda

```

That got my grub working but the UUIDs all over menu.lst where fubared, which was weird to me because I don't think I changed anything about my partitions.  Not sure.  Either way the following fixed menu.lst

```

sudo update-grub

```

Finally I added the Windwos 7 boot option back to menu.lst and I am 100% in business with sane booting.  My wife will be quite happy she no longer has to manually specify kernels to boot the machine.

---

