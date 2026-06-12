---
title: "Unmount USB drive? Or eject? Or even savely remove?"
date: 2009-11-22
forum: Desktop Environments
---

### Post by vlc on 2009-11-22
Hi *,

If I want to remove an USB drive from my PC, Gnome gives me three options in the desktop icon's context menu: *Unmount*, *Eject* and *Savely Remove Drive*.

Does anyone know what the differences are between these three options?

Thanks a lot in advance!

---

### Post by Janneman27 on 2009-11-23
I have no idea! But I think canonical should try and integrate these three things. I've also noticed that there are three options and I feel it is silly, confusing and unnecessary.

I love the improvements made in Karmic, but I hope that with 10.04 they will improve these little annoyances. I really believe that these small things are keeping lots of Windows user away from Ubuntu and that if these were fixed, the UI would feel like a true alternative to even the most hardcore of Win fans.

---

### Post by vlc on 2009-11-24
I think I found an explanation:

[https://bugzilla.gnome.org/show_bug.cgi?id=598690#c5]("https://bugzilla.gnome.org/show_bug.cgi?id=598690#c5")

Resuming:
[LIST]
[*]*Unmount* if you only want to unmount the drive but not remove it, e.g. to check the disk for errors
[*]*Eject* for CDs/DVDs to, well, eject them.
[*]*Savely remove* for USB drives et al. But there seems to be a bug with internal card readers. When savely removing a card from the card reader, the card cannot be mounted any more without reboot. Using *Eject* in this case works well.
[/LIST]

Cheers!

---

### Post by sabre2th on 2009-11-24
> **vlc said:**
> I think I found an explanation:

[https://bugzilla.gnome.org/show_bug.cgi?id=598690#c5](https://bugzilla.gnome.org/show_bug.cgi?id=598690#c5)

Resuming:
[LIST]
[*]*Unmount* if you only want to unmount the drive but not remove it, e.g. to check the disk for errors
[*]*Eject* for CDs/DVDs to, well, eject them.
[*]*Savely remove* for USB drives et al. But there seems to be a bug with internal card readers. When savely removing a card from the card reader, the card cannot be mounted any more without reboot. Using *Eject* in this case works well.
[/LIST]

Cheers!
That makes sense, but what exactly is the difference between 'Unmount' and 'Safely Remove'?  It still seems redundant to me for anyone that knows what 'unmount' is.

---

### Post by bmuluu on 2009-11-24
> **sabre2th said:**
> That makes sense, but what exactly is the difference between 'Unmount' and 'Safely Remove'?  It still seems redundant to me for anyone that knows what 'unmount' is.

Well, unmounting has to do with removing a device's filesystem from its mount-point on the computer's file system usually in */media/* or */mnt/*.
You can unmount a device so as to format it, or check it for errors.
The mount point in */media/* ceases to exist but the device is still listed in */dev/*

To safely remove a device implies it is going to be unmounted and won't be available as a device connected to the computer until it is plugged in again.

If you plug a flash drive into a USB port, its filesystem will be mounted on your filesystem. My mount point is */media/*

With a flash disk plugged in:
```
ls /dev/sd*
```returns
*/dev/sda  /dev/sda1  /dev/sda2  /dev/sda3  /dev/sdb  /dev/sdb1*

*/dev/sdb* is the flash drive

with the flash drive unmounted,
```
ls /dev/sd*
```still returns:
[I]/dev/sda  /dev/sda1  /dev/sda2  /dev/sda3  /dev/sdb  /dev/sdb1
[/I] 

yet if it is safely removed:
```
ls /dev/sd*
``` returns:
*/dev/sda  /dev/sda1  /dev/sda2  /dev/sda3*

---

### Post by yossell on 2009-11-24
Thanks - I'd wondered about that too, and now I think I understand.

---

### Post by blur xc on 2009-11-24
> **bmuluu said:**
> Well, unmounting has to do with removing a device's filesystem from its mount-point on the computer's file system usually in */media/* or */mnt/*.
You can unmount a device so as to format it, or check it for errors.
The mount point in */media/* ceases to exist but the device is still listed in */dev/*

To safely remove a device implies it is going to be unmounted and won't be available as a device connected to the computer until it is plugged in again.

If you plug a flash drive into a USB port, its filesystem will be mounted on your filesystem. My mount point is */media/*

With a flash disk plugged in:
```
ls /dev/sd*
```returns
*/dev/sda  /dev/sda1  /dev/sda2  /dev/sda3  /dev/sdb  /dev/sdb1*

*/dev/sdb* is the flash drive

with the flash drive unmounted,
```
ls /dev/sd*
```still returns:
[I]/dev/sda  /dev/sda1  /dev/sda2  /dev/sda3  /dev/sdb  /dev/sdb1
[/I] 

yet if it is safely removed:
```
ls /dev/sd*
``` returns:
*/dev/sda  /dev/sda1  /dev/sda2  /dev/sda3*

Ok, the difference between unmounting and safely removing makes sense to me.  But what does ejecting do to a usb device?

Also, I routinely unmount from the command line, it's the best and safest way (for me) to make sure the device can be removed safely, but how do you do the others from the command line?

Thanks,
BM

---

### Post by vlc on 2009-11-25
> **blur xc said:**
> Ok, the difference between unmounting and safely removing makes sense to me.  But what does ejecting do to a usb device?


I do see a difference between *Eject* and *Savely remove* with my internal card reader. When using *Savely remove* I cannot mount the card any more without a reboot. When choosing *Eject*, the card is automatically mounted again when inserted.

But I don't have any idea if USB devices are treated differently by *Eject* and *Savely remove*.

---

### Post by Pogeymanz on 2009-11-25
Just to clarify, this sounds like a Gnome problem and not Ubuntu's fault. Can someone correct me on that?

If I were you, I would always just use 'eject.' To be honest, if it is unmounted, there shouldn't be any reason that removing it is unsafe. The Linux kernel doesn't know the difference between USBs and CDs and Hard drives. Storage is either mounted- so you can read and write to it, or it isn't mounted- so you can't do anything to it. If you can't read or write to something, I can't imagine that unplugging it will do any damage.

---

### Post by vlc on 2009-11-26
> **Pogeymanz said:**
> Just to clarify, this sounds like a Gnome problem and not Ubuntu's fault.

I agree. Looks more like a Gnome-specific issue.

> **Pogeymanz said:**
> If I were you, I would always just use 'eject.'

This is actually exactly what I'm doing.

Cheers!

---

