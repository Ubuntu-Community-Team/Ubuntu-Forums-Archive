---
title: "10 second boot gap"
date: 2009-05-24
forum: General Help
---

### Post by rocketman768 on 2009-05-24
Using bootchart, I have found out that there is a 10 second gap in the middle of my boot process. However, I don't know what's causing it. The dmesg isn't much help:

```

[   16.700153] ppdev: user-space parallel port driver
[   26.769234] /build/buildd/linux-2.6.28/drivers/hid/usbhid/hid-core.c: usb_submit_urb(ctrl) failed

```

Does someone know how I can figure out what is happening between 16 and 26 seconds?

---

### Post by Greenwidth on 2009-05-26
Similarly, I have a (nearly) 12 sec gap before the boot seems to kick in..

---

### Post by Legace on 2009-05-26
Try disconnecting your printer (or any other device on the parrarel port) and see how it goes..

---

### Post by rocketman768 on 2009-06-16
Actually, found out that it was my USB joystick. Logitech Extreme 3D Pro.

---

### Post by rocketman768 on 2009-06-16
> **Greenwidth said:**
> Similarly, I have a (nearly) 12 sec gap before the boot seems to kick in..

For me, I disable legacy USB in my BIOS, and that fixed the initial boot gap.

---

