---
title: "Trying (and failing) to install Ubuntu...help!"
date: 2009-01-30
forum: General Help
---

### Post by doctorbighands on 2009-01-30
Here's the deal with the machine I'm trying to install to. It has:

-A built-in but not functioning CDROM drive
-A fully functional floppy drive
-A USB CDROM drive

There is no option in the BIOS to boot from USB.

I have tried going this route ([https://help.ubuntu.com/community/Installation/FromHardDriveWithFloppies](https://help.ubuntu.com/community/Installation/FromHardDriveWithFloppies)), but I can't get tomsrtbt to install to a floppy. I'm running XP, so no DOS mode, and in Ubuntu I get read errors (on brand new disks).

I'm at my wits' end here, and I don't know how to proceed. A network install is MILES over my head, so that isn't an option for me, either.

Is there a distro other than tomsrtbt that would work here? If not, what do I do to get Ubuntu installed on this laptop?

---

### Post by kmac on 2009-01-30
[http://ubuntuforums.org/showthread.php?t=28948](http://ubuntuforums.org/showthread.php?t=28948)

---

### Post by doctorbighands on 2009-01-30
> **kmac said:**
> [http://ubuntuforums.org/showthread.php?t=28948](http://ubuntuforums.org/showthread.php?t=28948)

This looks helpful, but it wouldn't work in my situation because there is no operating system currently installed on the target machine.

---

### Post by kmac on 2009-01-30
Ouch.

Try downloading DOS to floppy first, maybe?

Or even just plain unix/bash

---

### Post by doctorbighands on 2009-01-30
I'm not sure what that means. Would it really help me to install DOS first?

I'm still quite stuck. How frustrating!

---

### Post by kmac on 2009-01-30
If you have a living ubuntu installation, try:

[http://www.pendrivelinux.com/usb-ubuntu-804-persistent-install-from-linux/#more-401](http://www.pendrivelinux.com/usb-ubuntu-804-persistent-install-from-linux/#more-401)

---

### Post by doctorbighands on 2009-01-30
The target machine can't boot from USB.

---

### Post by kmac on 2009-01-30
Not even from pen drive?

---

### Post by kmac on 2009-01-30
This should help, sorry for all the confusing loops and such.

[http://www.pendrivelinux.com/use-a-floppy-to-boot-usb-pendrive-linux/](http://www.pendrivelinux.com/use-a-floppy-to-boot-usb-pendrive-linux/)

---

### Post by doctorbighands on 2009-01-30
There's no option in the BIOS allowing me to boot from any USB device.

---

### Post by Boycraft on 2009-01-30
I know! I know! Look for a "boot from other devices option". Turn it on. Try.
Once I've tried to install OS with usb keyboard. Keys didn't work. Then one man told me to turn on something like USB-sth-sth and the keyboard would work. I found one, it was "USB legacy support". Maybe something like that to turn on?

---

### Post by kmac on 2009-01-30
He might just have a board or bios that doesn't support it. I don't know if you got my last link for using floppy to boot from usb, as you posted at the same time as me. Go back to the first page and click the last link i sent you

---

### Post by The Riddler on 2009-01-30
Even though you say it is over your head, network install might be your best option.

I suppose you might also be able to remove the HDD from the laptop, and plug it into another box and install it there. Put the HDD back in and it *should* boot.

---

### Post by doctorbighands on 2009-01-30
I'm trying to make a boot floppy based on the instructions on the pendrivelinux site, but there's a problem:

The command```
gzip -dc pdlfloppy.img.gz | dd of=/dev/fd0
```doesn't seem to write anything to the floppy disk.

---

### Post by kmac on 2009-01-30
Please post results of

```

gzip -dc[COLOR="Red"]**v**[/COLOR] pdlfloppy.img.gz | dd of=/dev/fd0
```

---

### Post by doctorbighands on 2009-01-30
> **kmac said:**
> Please post results of

```

gzip -dc[COLOR="Red"]**v**[/COLOR] pdlfloppy.img.gz | dd of=/dev/fd0
```

I get the following output, but the floppy drive remains idle.
```
pdlfloppy.img.gz:	 64.0%
2880+0 records in
2880+0 records out
1474560 bytes (1.5 MB) copied, 0.102155 s, 14.4 MB/s
```

---

### Post by kmac on 2009-01-30
Is /dev/fd0 where your floppy disk actually is or is that what was in the tutorial?

```
 ls /dev/fd* 
```

and post the output if you're not sure

---

### Post by doctorbighands on 2009-01-30
Output is```
/dev/fd0

/dev/fd:
0  1  2  3  5

```
So it looks like that's where it is.

I tried to mount the drive, but the terminal tells me /dev/fd0 isn't a block device. I've been able to mount it successfully before, so I don't know what the issue is there.

EDIT: I just tried a reboot. I tried mounting /dev/fd0, and now it says "special device /dev/fd0 does not exist". I know there's nothing wrong with my floppy drive - it works fine in windows, and I've had it working in Ubuntu as well.

---

### Post by kmac on 2009-01-30
How are you trying to mount it?

---

### Post by doctorbighands on 2009-01-30
> **kmac said:**
> How are you trying to mount it?

```
sudo mount /dev/fd0
```

or

```
sudo mount -t vfat /dev/fd0 /media/floppy0
```

because /etc/fstab says that /media/floppy0 is where it should mount to. The output of both of those commands is the same: "mount: special device /dev/fd0 does not exist"

---

### Post by kmac on 2009-01-30
Hmm... weird...

I'm sorry bud, but I have to hit the sack. I'm meeting a friend early tomorrow morning that I haven't seen in years.

Try googling any error messages you get. Be sure to "put them in quotes" to find your answers faster.

I'm sorry I can't be of much more help tonight. If you don't have it by tomorrow (Eastern Time) PM me and I'll keep helping you out.

---

