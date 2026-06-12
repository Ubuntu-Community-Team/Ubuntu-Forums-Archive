---
title: "Unmounting my USB hard drive is strange"
date: 2005-10-18
forum: Desktop Environments
---

### Post by André on 2005-10-18
Hi everybody,

i just plugged in my USB disk and everything went fine.

Mounted to /media/usbdisk and icon appears on the desktop.

But when i click to unmount my USB disk it tells me that it wasn´t able to eject it.

Any ideas how to tell my computer that this is not a CD ROM drive?

It´s absolutely no show stopper but quite disturbing to get an error message everytime i unmount.

Greetings
Andr´e

---

### Post by rmjokers on 2005-10-18
Is it possible that there is an application open that is using a file on the USB drive?  That is the only thing I could think of that might cause a problem like this.

---

### Post by André on 2005-10-18
Hi,

you get a different message, when you still using a file.

It unmounts the usbdisk and it is save to turn it off but it just displays this message.

Greetings
Andr´e

---

### Post by Poldi on 2005-11-07
ping.

any soloution to this yet?

I share the same problem for 2 external USB disks that worked fine with 4.10 and 5.04. mind you - apart from the annoying message it is working still.

one hint: I have done an online dist-upgrade from Hoary to Breezy - I wonder if this makes a difference?

kind regards,
Carsten

---

### Post by eeried on 2005-11-14
I have exactly the same problem with two computers with two different upgrade methods: one on-line and the other with the install CD.

Both computers were fine with Hoary. 

With Breezy, only cds eject fine.
Whatever else is mounted -- Zipdisk (USB), floppy both internal and USB  -- doesn't "eject" (the phrase "Unmount volume" occurred once in the context menu,  it's more often "Eject". Eject or unmount produce a small popup saying the device can't be ejected.

But as has been pointed out the devices do seem to get unmounted.

However it is very annoying -- Hoary  unmounted so smoothly! 

Any ideas?

---

### Post by aysiu on 2005-11-14
You may have to file a bug report on it.
If it's [what happened to me](http://www.ubuntuforums.org/showthread.php?t=84262), I've already filed one.

---

### Post by Samuel on 2005-11-14
i had usb disk problems but today i needed to use the disk and i added the following into fstab and i no longer get the error when i try to unmount it

```
/dev/sda1    /media/sda1   auto   rw,user,noauto    0  0
```

not sure its the right way to do it but it works for me

---

### Post by eeried on 2005-11-15
Thanks for the link aysiu! I didn't hit on that thread when i serached for umount problems.

As was pointed out in that thread, it really looks like a "Gnomic"  bug since unmounting was fine on two different computers with Hoary (a laptop and a desktop). However I can manually unmount the internal floppy as user (I mount it manually otherwise it doesn't mount automatically but I don't care -- I rather like the command line).

Cheers,

---

