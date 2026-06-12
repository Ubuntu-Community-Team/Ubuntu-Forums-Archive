---
title: "[SOLVED] where to mount my USB raid to?"
date: 2008-12-19
forum: General Help
---

### Post by xarte on 2008-12-19
the example I'm following uses /dev/md0 /var/media auto defaults 0 3 added to fstab so that it auto mounts on boot -

which gives me a 'var/media doesn't exist' error when I tried to mount it in the terminal.

I have an 'include/media' and a 'drivers/media'

BTW it was a really fun learning exercise. The example used sda1 as one of the devices (which is the designation of my hard drive! - luckily it queried so I could hit q) ... took a while to get the drives correctly identified, formatted and flagged, correct syntax and all that stuff. Just need to get it mounted.

---

### Post by ohzopants on 2008-12-19
I would highly recommend you mount it under /media.  By default this is where ubuntu will mount usb sticks, cds, dvds, ipods...  For example my ipod (named Atlas) gets mounted to /media/Atlas and my cd drive gets mounted to /media/cdrom.

The first thing you need to do is create a mount point:
```

sudo mkdir /media/USBRAID

```

Then chage "/var/media" to "/media/USBRAID" in your fstab.  Of course you can call it whatever you want, I just picked USBRAID at random.

To test it out without rebooting you can do:
```

mount -a

```

(I can never remember if you need sudo for that or not)

---

### Post by xarte on 2008-12-19
ah!!! mkdir! now that you tell me, its SO screamingly obvious - no wonder the examples I found were mounting to interestingly named directories. Sheesh. I was up till 1am trying to get this thing to work ...

you're a gem, a thousand thank-yous!

I end up just going to su... probably not good practice but I get sick of typing my password!

---

### Post by xarte on 2008-12-19
I did it! w00t!  happy dance. I'll have to do it again to see if I actually know what I'm doing know. But it's mounted, and re-mounted after reboot.

I tried copying a file to it but permission denied - can I change permissions on it and just use it as a regular drive? I can't find the command to do so.

Since it's just a simple two-stick drive I'm not sure that there's any advantage to hanging onto it - I guess I should just use them as normal USB drives, since it's hardly archive-worthy. Fun exploring the concept without breaking anything.

---

### Post by ohzopants on 2008-12-19
You can set the permissions for the drive directly in your fstab.  I don't know the exact syntax, but with a little research it shouldn't be too hard to find.

Changing ownership of the mount point so that it belongs to you may also solve the problem.
```

sudo chown youruser:youruser /path/to/mount/point

```

---

