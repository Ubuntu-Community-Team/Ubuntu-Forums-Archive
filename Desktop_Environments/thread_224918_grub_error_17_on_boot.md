---
title: "grub error 17 on boot"
date: 2006-07-28
forum: Desktop Environments
---

### Post by piercy on 2006-07-28
on boot i get a grub error 17.  i know what caused the problem its ine the grub menu.lst where i was trying to get it to have an option for booting windows.(im a noob lol) i just need ot get back into ubuntu to delete the entry.  anyway to go around grub? i have 2 hard drives one has windows 98 on one has ubuntu desktop 6.06. i have unplugged the windows one for now just so i dont mess it up like i did earlier on today.  any ideas on how to go around grub or how to boot into ubuntu?

when i boot it says:
```

GRUB loading stage 1.5.


GRUB loading, please wait...
Error 17
```

then it just does not do anything.

---

### Post by bulldog on 2006-07-28
You can try to startup with the live CD and mount your /
Then you can edit your grub menu.
I don't know if there is a simpler way of doing this.
You should edit a line for windows like this:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

Ofcourse you should use your own parameters for /dev/hda1 and the type of Windows.

---

### Post by piercy on 2006-07-28
start up with live cd.. you eman put it in and select boot from hard drive one? or select run/install?  boot from hard drive gives me the error again.  i havent tried run/install because i thought that would be the live cd version rather than my stored version?

---

### Post by piercy on 2006-07-28
just saw your edit.  so how do i find out what values to replace /dev/hda1 ??

---

### Post by bulldog on 2006-07-28
Yes you should run the live CD, not your existing install.
When it runs mount your existing / to a folder.
Then you should be able to edit your grub menu.lst.

You know what kind of hdd's you have and your partitions.
If you use only IDE hdd's then the first one is hda and the second one is hdb.
If you have SATA it would be sda.

---

### Post by piercy on 2006-07-28
erm i double clicked it to try mount but it said it couldnt mount.

```

Unable to mount the selected volume.

error: device /dev/hda1 is not removable
error: could not execute pmount

```

---

### Post by bulldog on 2006-07-28
I have not much experience with this but try in console,

mount /dev/hda1 /mnt/hda1

I'm not sure of this works out because I never used the live CD.
But trying doesn't hurt I think.

---

### Post by piercy on 2006-07-28
```

mount: mount point /mnt/hda1 does not exist

```

thats what i got when i did sudo mount /dev/hda1 /mnt/hda1

---

### Post by bulldog on 2006-07-28
Is there a possebillity to make a folder named hda1?
That's what's wrong,the folder to mount at,doesn't exist.
But I,m not sure if you can make a folder with the live cd.
Like i said I never fooled around with the live CD.
Could you reinstall grub from the live CD?

---

### Post by piercy on 2006-07-28
u clever clever person :D i created a oflder named hda1 and mounted the disk to it :D thanks

edit: changed 2 person

---

### Post by piercy on 2006-07-28
now i have the problem that i cannot save the menu.lst.  i saved the changed menu.lst to the live cd desktop.  is there any sort of terminal command to move it? maybe that will bypass the privilages if i use sudo.

---

### Post by bulldog on 2006-07-28
Strange...........you can edit it but not save it.
You use sudo I presume?
You need root acces to that drive and to altered it.

sudo cp /Desktop/menu.lst /mnt/hda1/boot/grub/menu.lst

---

### Post by piercy on 2006-07-28
you seme to have misunderstood. i have read access to the hard drive but i cannot save there.  i didnt use the terminal at all to edit it. i just browsed to it opened it, edited it and then saved it to the livecd desktop. so the "corrupt version" is still there.  is there a way to move the clean version into the correct folder to replace the "corrupt version"?

---

### Post by piercy on 2006-07-28
i think i might have done it sudo mv desktop/menu.lst  ~/hd/grub/menu.lst just checking now.


nope same error on boot im goign back onto live cd now.

---

### Post by bulldog on 2006-07-28
You should use the terminal and type

sudo gedit /mnt/hda1/boot/grub/menu.lst

So you can edit the original menu.
When done just save it and if you do it right then you can boot again.

---

### Post by piercy on 2006-07-28
ok my edit seemed ot have worked os that isnt the problem now.  my disk is showing up as /dev/hda with no 1. so does that mean that grub should say hd(0,-1)? i know this sounds stpid but i dunno what the problem is.

---

### Post by bulldog on 2006-07-28
title		Ubuntu, kernel 2.6.15-26-k7
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-26-k7 root=/dev/sda1 ro quiet splash vga=792
initrd		/boot/initrd.img-2.6.15-26-k7
savedefault
boot

This is my entry in grub to boot.
Grub is on my first hdd  [hd1,0] and my Ubuntu is on my Sata hdd [sda1].
If you have one hdd then it should be hd1,0.
On which partition is Ubuntu installed?
If you have just one parttion then it should say on the third rule root=/dev/hda1 ro quiet splash.

---

### Post by piercy on 2006-07-28
mine was exactly the same as yours.  im going to try install grub on the live cd version lol i dunno who this will work. but if it install the i can steal the original menu.lst ill post back in a bit.

---

### Post by piercy on 2006-07-28
it said it installed but i dont think it did because i cant find it. do you know how to do a reinstall using apt-get? im gonna try find menu.lston the internet

---

### Post by bulldog on 2006-07-28
sudo apt-get install grub

But what have you changed at your original menu.lst?
It should be easy to fix if you know the details.

---

### Post by piercy on 2006-07-28
menu.lst :
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
timeout		30

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
# kopt=root=/dev/hda1 ro

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


title		Ubuntu, kernel 2.6.15-26-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot


### END DEBIAN AUTOMAGIC KERNELS LIST

```
ok thats the menu.lst if i look in disks manager under partitions it say /dev/hda1/ can you just check that the above is ok and i ahvent made any mistakes.  i know it slightly long winded.  sorry, please and thanks :)

---

### Post by bulldog on 2006-07-28
Looks alright to me.
You could put the recovery mode at it,but it makes no difference I think.

title		Ubuntu, kernel 2.6.15-26-k7 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-26-k7 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.15-26-k7
boot

Just change my k7 for yours and sda1 into hda1 
Make sure there is a empty space between them [boot and recovery]
Then it should work.

---

### Post by piercy on 2006-07-28
ok im rebooting now

---

### Post by piercy on 2006-07-28
still no luck :( any ideas what will happen if i just delete the whole grub folder?

i fear were nearing the end of the road.

---

### Post by bulldog on 2006-07-28
Are you sure that your kernel is the right one?
Ofcourse if you haven't any important things on your drive you can do a fresh install.
But your grub menu.lst seems to be allright.
There should be a minor thing that's not good.
You are certain that you editted the menu.lst at mnt/hda1/boot/grub/menu.lst?
So that you did not make a new .txt document that is not used by grub?
Otherwise I don't know what is going wrong here.:sad:

---

### Post by poppers1957 on 2007-06-17
just a little tip someone gave me...........alt+F2  enter sudo nautilus       <<<this if you're using nautilus,  or sudo konqueror     <<<if you'r using konqueror.  It will help you edit and save things without not being able to save them for you.  Sometimes things won't get saved and you won't know it.  This will help with that.  But from what I've read, I believe your kernel listing may be wrong.   Keep us posted please.

---

