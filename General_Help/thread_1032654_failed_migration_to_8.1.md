---
title: "failed migration to 8.1"
date: 2009-01-06
forum: General Help
---

### Post by jonbjarna on 2009-01-06
Hi

I am using AMD 64 bit dual core machine.
I have been using ubuntu 8.04 server edition for a while without any problems. I am using raid.

I tryed to migrate my server from 8.04 to 8.1. It stopped at some point and I rebooted. It had not changed the kernal file so my old system 8.04 was still there.
However, I can not boot the server, I get the following error:
[B]Starting up..
Aperture pointing to e820 RAM. Ignoring
Your BIOS doesn't leave a aperture memory hole
Please enable the IOMMU option in the Bios setup
This costs you 64 MB of RAM
Kernel panic - not syncing: VFS: unable to mount root fs on unknown-block(0,0)[/B]

None of the other kernals worked, same message on the recovery kernal for the most current kernal.

I saw a post where someone suggested a BIOS upgrade, I now have ths most reasent BIOS but the problem is still there. 

Also saw that someone suggested installing some packages again after booting ubuntu from cd.
The thing is, when I try to use rescue from the cd, and choose md0 as my root, commands like find, locate etc, can not be found.
I have searched, but not found any instructions on how I can use the rescue procedure to be able to install packages onto my disk.
Can anyone help me out ?

---

### Post by fjgaude on 2009-01-06
Likely your **menu.lst** file in /boot/grub is pointing at the wrong drive or install. The error shows just as the BIOS points to the drive that should have the bootup code.

---

### Post by jonbjarna on 2009-01-06
> **fjgaude said:**
> Likely your **menu.lst** file in /boot/grub is pointing at the wrong drive or install. The error shows just as the BIOS points to the drive that should have the bootup code.

Thanks.

Do you know how I can fix that ?

Regards
Jon

---

### Post by fjgaude on 2009-01-06
You have to know what drives are called, and from which one the bootup occurs from.

Show what **df -h** is, but has to be done from a liveCD, since you can't boot.

I take it you are didn't finish to upgrade... wow, not good!

From a liveCD you can examine the /etc/fstab file, show it to us; and then show us the /boot/grub/menu.lst file, just that last 30 or so lines.

Also, what kind of raid are you using?

---

### Post by maestrobwh1 on 2009-01-06
If you can get into your drive with a live cd, and you think you may have answered "n" to install the maintainer's version of this file: 

/etc/init.d/mountkernfs.sh

I found I frequently am left with an unbootable system.  If you answered no, you might have a similar file there called by the same name, but terminated with something like mountkernfs.sh-upgrade.  

If so, rename the mountkernfs.sh to something else and rename the -upgrade file to mountkernfs.sh and try booting.  

It is a shot in the dark, but it sounds like you are crippled anyway.

As far as grub pointing to the wrong thing:
You might have luck with SuperGrubDisk
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by jonbjarna on 2009-01-06
Thanks

The upgrade did not finish... it failed.
I managed to get things working with the rescue boot from the CD, aperantly I needed to mount my /usr (its on a separate drive.)
I found the menu.lst and saw that it had been edited, so I renamed the menu.lst~ to menu.lst and booted
Got a new error, read only file system...

I'm using software raid.
I'll have to find a way to transfer the output you asked for...
How do I mount a usb memory stick, do you know ?



> **fjgaude said:**
> You have to know what drives are called, and from which one the bootup occurs from.

Show what **df -h** is, but has to be done from a liveCD, since you can't boot.

I take it you are didn't finish to upgrade... wow, not good!

From a liveCD you can examine the /etc/fstab file, show it to us; and then show us the /boot/grub/menu.lst file, just that last 30 or so lines.

Also, what kind of raid are you using?

---

### Post by jonbjarna on 2009-01-06
Hi, thanks.

The file seems intact and the date (April 2008) is older so I guess it's ok. 
There is another file there with the suffix dpkg-new, it's younger (Oct 200)

Regards
Jon

> **maestrobwh1 said:**
> If you can get into your drive with a live cd, and you think you may have answered "n" to install the maintainer's version of this file: 

/etc/init.d/mountkernfs.sh

I found I frequently am left with an unbootable system.  If you answered no, you might have a similar file there called by the same name, but terminated with something like mountkernfs.sh-upgrade.  

If so, rename the mountkernfs.sh to something else and rename the -upgrade file to mountkernfs.sh and try booting.  

It is a shot in the dark, but it sounds like you are crippled anyway.

As far as grub pointing to the wrong thing:
You might have luck with SuperGrubDisk
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by Slim Odds on 2009-01-06
> **jonbjarna said:**
> There is another file there with the suffix dpkg-new, it's younger[COLOR=Red] (Oct 200)[/COLOR]

Dang, that's an OLD file.  :D

---

### Post by jonbjarna on 2009-01-06
:) 2008...

Do you know what device I use for usb ?
I need to mount -t usbfs /dev/??? /usb

> **Slim Odds said:**
> Dang, that's a OLD file.  :D

---

### Post by Slim Odds on 2009-01-06
> **jonbjarna said:**
> :) 2008...

Do you know what device I use for usb ?
I need to mount -t usbfs /dev/??? /usb

Try: lsusb or sudo lsusb

---

### Post by jonbjarna on 2009-01-07
Hi
These do not exist in /dev
tryed all of the /dev/sd* devices, nothing works.
Set up an alternate ftp server to do this, i'll figure out the usb thing later....

> **Slim Odds said:**
> Try: lsusb or sudo lsusb

---

### Post by jonbjarna on 2009-01-07
Hi

The output is attached.
Also attached the menu.lst~ file

Thanks
Jon

> **fjgaude said:**
> You have to know what drives are called, and from which one the bootup occurs from.

Show what **df -h** is, but has to be done from a liveCD, since you can't boot.

I take it you are didn't finish to upgrade... wow, not good!

From a liveCD you can examine the /etc/fstab file, show it to us; and then show us the /boot/grub/menu.lst file, just that last 30 or so lines.

Also, what kind of raid are you using?

---

### Post by Slim Odds on 2009-01-07
> **jonbjarna said:**
> Hi
These do not exist in /dev
tryed all of the /dev/sd* devices, nothing works.
Set up an alternate ftp server to do this, i'll figure out the usb thing later....

Sorry to confuse you. lsusb is a command

Try:```
sudo lsusb
```

---

### Post by jonbjarna on 2009-01-07
Oh, stupid of me.

Saw the stick using lsusb
bus 001 device 003 .....
Can that be translated to a device on /dev ?
Sorry for my stupit questions....



> **Slim Odds said:**
> Sorry to confuse you. lsusb is a command

Try:```
sudo lsusb
```

---

### Post by fjgaude on 2009-01-07
I notice in your df -h readout that there is two USBs: /dev/sdc and /dev/sdd. Try one of those.

Gosh, are they all in an **md** raid array?

---

### Post by jonbjarna on 2009-01-07
Hi
Tryed that, dosent seem to work, I'll try to figure out why when I get the sever up and running.

I have 4 sata disks in 2 arrays.

Regards
Jon

> **fjgaude said:**
> I notice in your df -h readout that there is two USBs: /dev/sdc and /dev/sdd. Try one of those.

Gosh, are they all in an **md** raid array?

---

### Post by fjgaude on 2009-01-07
Are the arrays made up of the USB drives?

---

### Post by jonbjarna on 2009-01-08
No, SATA disks.


> **fjgaude said:**
> Are the arrays made up of the USB drives?

---

### Post by fjgaude on 2009-01-08
Okay, and gosh! You are booting from an **mdadm** raid1 array.

When you updated the installer likely didn't figure on this. You might try using **grub** command to put grub in your boot MBR:

```
sudo grub
grub>find /boot/grub/stage1
grub>root (hd0,0)
grub>setup (hd0)
grub>quit
```

The **find** command within grub will show where you have bootable code. Use the one that is right for you. It looks like what I have here is what you want: hd0,0.

then if necessary, out of grub and onto another command line:

```
sudo grub-install /dev/sda
```

I hope this is an aid and a fix. There is so much to learn when you are doing things like booting from a software raid1 array!

---

