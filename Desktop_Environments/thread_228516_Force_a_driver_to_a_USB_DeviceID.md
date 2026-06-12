---
title: "Force a driver to a USB DeviceID?"
date: 2006-08-03
forum: Desktop Environments
---

### Post by nocturn on 2006-08-03
How can I force a driver (Usblp in my case) to a certain usb deviceID?

I need to do this because a printer I need to use does not identify itself correctly as a usb-printer class device.

---

### Post by jordilin on 2006-08-03
Perhaps the following thread is what you are looking for:
[http://ubuntuforums.org/showthread.php?t=91948](http://ubuntuforums.org/showthread.php?t=91948)

---

### Post by nocturn on 2006-08-04
> **jordilin said:**
> Perhaps the following thread is what you are looking for:
[http://ubuntuforums.org/showthread.php?t=91948](http://ubuntuforums.org/showthread.php?t=91948)


Thanks Jordilin

But my problem is different.
I have a printer that does not identify itself as a printer, so the usblp module does not get loaded or linked to it.

I know there must be a way to tell udev/hotplug to use a specific driver for a specific usbid, I just cannot find it.

---

### Post by jordilin on 2006-08-04
What printer model do you have?

---

### Post by nocturn on 2006-08-04
A Canon MPC200 (multifunctional)

---

### Post by jordilin on 2006-08-04
I've been looking around the net and this will be a difficult thing. It seems that Ubuntu does not recognize your printer, so it does not load the driver. This guy [http://lists.freestandards.org/pipermail/printing-user-samsung/2004/001087.html](http://lists.freestandards.org/pipermail/printing-user-samsung/2004/001087.html)
seems to have the same issue as you.
Has you tried to load the proper module in the kernel at boot up?

---

### Post by nocturn on 2006-08-04
> **jordilin said:**
> I've been looking around the net and this will be a difficult thing. It seems that Ubuntu does not recognize your printer, so it does not load the driver. This guy [http://lists.freestandards.org/pipermail/printing-user-samsung/2004/001087.html](http://lists.freestandards.org/pipermail/printing-user-samsung/2004/001087.html)
seems to have the same issue as you.
Has you tried to load the proper module in the kernel at boot up?

Thanks Jordilin

I tried to load usblp manually, but I need a way to associate the driver with that deviceID.  Normally this happens when it identifies as an usb-printer class, but this one doesn't do that.

The cardreader in front of the printer is detected though (usb-storage).

---

### Post by vilain_mamuth on 2007-06-11
hi,

i have the same problem as you in Feisty.
i tried to build udev rules to force MPC200 to have the device /dev/canon_mpc200 (or whatelse like /dev/lp0) but it makes me headaches too

did you find a way for this model to work?

thx

---

