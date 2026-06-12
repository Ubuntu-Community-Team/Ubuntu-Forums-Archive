---
title: "Accidentally Nuked My Menu.lst (grub)"
date: 2006-09-30
forum: Desktop Environments
---

### Post by gabrieliscool on 2006-09-30
Can Someone please help me restore my menu.lst 
here is my setup:
i have 2 hard drives
the first hard drive has two partitions
the first partition has xp the second is for back up
the second hard drive has ubuntu (the desktop Version) installed
(note: i let the installed decide how to allocate space on the seconds hard drive, so it's has two partitions)

thanks

p.s. double thanks

---

### Post by djRobbieF on 2006-09-30
Hmmm, let's see if we can give this a go.  It may take a couple tries...

I'll need to know the output from ```
uname -r
```

---

### Post by djRobbieF on 2006-09-30
Here's try #1, which may work if you're running the default Ubuntu 386 kernel:

```

default		0
timeout		10

title		Ubuntu, kernel 2.6.15-23-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sdb1 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin 
boot

title		Other operating systems:
root

title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

Does that work?

---

### Post by gabrieliscool on 2006-09-30
2.6.15-27-386

---

### Post by djRobbieF on 2006-09-30
OK let me modify the first sample then...

---

### Post by djRobbieF on 2006-09-30
Try this one (try #2, based on the output of your uname -r)

```
default		0
timeout		10

title		Ubuntu, kernel 2.6.15-27-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/sdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/sdb1 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin 
boot

title		Other operating systems:
root

title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

---

### Post by gabrieliscool on 2006-09-30
thanks, i figured out how to make  it boot.

last favor, can you attach a copy of your menu.lst, because i want to add a bacground image.

---

### Post by djRobbieF on 2006-09-30
?  Mine?  Why would mine have a background image?  ;)

And mine will not work with your system.

If you must though... and because I'm so eager to please...
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
# kopt=root=/dev/sda2 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-27-686
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-686 root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-686
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-686 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-686 root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.15-27-686
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

---

### Post by gabrieliscool on 2006-09-30
thank you very much, my start up is just as before.

thanks

---

### Post by djRobbieF on 2006-10-01
np

---

### Post by antonio.spadim on 2007-12-02
> **gabrieliscool said:**
> thanks, i figured out how to make  it boot.

last favor, can you attach a copy of your menu.lst, because i want to add a bacground image.

Could you sai how? I have the same problem.

---

### Post by PmDematagoda on 2007-12-02
Concerning that, in my menu.lst file, this is the entry that allows a splash screen on GRUB:-

```
splashimage=(hd0,0)/boot/grub/Ubuntusplash.xpm.gz

```

(hd0,0) is the root where the file is located and the rest is the path of it.

And you do realise that posting on a year old thread is not the best way to solve your problem do you?

---

### Post by jflaker on 2007-12-02
> **gabrieliscool said:**
> thank you very much, my start up is just as before.

thanks

Now make a backup before messing with it again.....:lolflag:

---

### Post by sandysandy on 2007-12-02
> **PmDematagoda said:**
> Concerning that, in my menu.lst file, this is the entry that allows a splash screen on GRUB:-

```
splashimage=(hd0,0)/boot/grub/Ubuntusplash.xpm.gz

```

(hd0,0) is the root where the file is located and the rest is the path of it.

And you do realise that posting on a year old thread is not the best way to solve your problem do you?

hi

for the splash image is the file type [COLOR="Blue"]xpm.gz [/COLOR]necessary or [COLOR="Blue"]png[/COLOR] file type is ok.
also what is [COLOR="Blue"]xpm.gz[/COLOR] type of file. where can i get info on different file types and their equivalent with Microsoft windows file types.

thanks

---

### Post by PmDematagoda on 2007-12-02
> **jflaker said:**
> Now make a backup before messing with it again.....:lolflag:

Sorry, but do you know that you are replying to a year old thread?

---

### Post by sandysandy on 2007-12-02
hi

i tried splash image of [COLOR="Blue"]png[/COLOR] type. during bootup my [COLOR="Blue"]png[/COLOR] file type was not read.

can u help me out. which all file types are read for splash image during startup.

regards

---

### Post by PmDematagoda on 2007-12-02
I cannot believe that this is on a one year old thread whose topic does not even concern what is being discussed:-k.

Anyway sandysandy, from what I have known and used, the only format that I know works as a splash screen for GRUB is .xpm.gz.

---

### Post by sandysandy on 2007-12-02
thanx for ur prompt reply.

i know its a one year old thread from ur earlier posts.
but it seems to be solving problems, however unrelated, so should be fine.
one more not related question. how does one get the splash image of.[COLOR="Blue"]xpm.gz[/COLOR].type.

regards

---

### Post by PmDematagoda on 2007-12-02
Not really sure about that, the one I have was already made, so I just downloaded it and set it up to work on GRUB.

---

