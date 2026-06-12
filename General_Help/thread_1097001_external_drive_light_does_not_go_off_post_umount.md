---
title: "external drive light does not go off post umount"
date: 2009-03-15
forum: General Help
---

### Post by vikrant_me on 2009-03-15
Even after i unmount my maxtor portable the light on the drive remains on, this usually goes off post "unmount" in windows, wondering why this happens.

---

### Post by dje on 2009-03-15
try the following from a terminal:
```
sudo eject *mountpoint of hard drive*
```

hope that helps,
dje

---

### Post by sgosnell on 2009-03-15
The light on the drive should be on as long as it's receiving power, whether or not it's mounted by the OS.  If it goes out under Windows, it's because Windows is killing the USB port, and Linux doesn't do that by default.

---

### Post by mb_webguy on 2009-03-15
It's not a bug.  It's an undocumented feature.  ;)

Don't worry.  It's perfectly normal for the light to remain on after the drive has been unmounted, because it is still receiving power.  Windows cuts off the power when it unmounts a USB device, while Linux doesn't.  Personally, I prefer the Linux method, since I can charge rechargable devices (like my phone) without mounting them.

---

### Post by vikrant_me on 2009-03-16
> **sgosnell said:**
> The light on the drive should be on as long as it's receiving power, whether or not it's mounted by the OS.  If it goes out under Windows, it's because Windows is killing the USB port, and Linux doesn't do that by default.

How do i "kill" the USB port in linux then?

---

### Post by sgosnell on 2009-03-16
Why do you want to?  I've never tried to do that.  It's probably possible, but I have no interest in doing it.

---

