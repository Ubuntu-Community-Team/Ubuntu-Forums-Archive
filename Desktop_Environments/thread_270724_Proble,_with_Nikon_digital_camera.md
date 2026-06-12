---
title: "Proble, with Nikon digital camera"
date: 2006-10-03
forum: Desktop Environments
---

### Post by idn on 2006-10-03
Hi, when i plug in my camera, I get the following error

```
An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device.
```

The camera is a Nikon coolpix s6, and it used to work fine but since has stopped working, any ideas?

---

### Post by ibob on 2006-10-03
Just thought I would chuck my thoughts in... The error looks like both Ubuntu and your camera where trying to read the memory card at the same time.

can you take the memory out the camera and read it that way?

---

### Post by idn on 2006-10-04
Don't have a memory card reader :(

---

### Post by raintheory on 2006-10-30
Not sure if this might help but may be worth a shot:

[http://ubuntuforums.org/showthread.php?t=286730](http://ubuntuforums.org/showthread.php?t=286730)

---

### Post by idn on 2006-11-27
> **raintheory said:**
> Not sure if this might help but may be worth a shot:

[http://ubuntuforums.org/showthread.php?t=286730](http://ubuntuforums.org/showthread.php?t=286730)

That worked great for me!

---

