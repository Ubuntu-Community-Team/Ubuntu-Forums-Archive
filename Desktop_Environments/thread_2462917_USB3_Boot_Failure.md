---
title: "USB3 Boot Failure"
date: 2021-05-30
forum: Desktop Environments
---

### Post by Geoff_Lane on 2021-05-30
Ubuntu 20:04 LTS Live Image

Folks,

I have an older Toshiba Satellite laptop with 18:04 as my main system (dual boot with Win10 which I never use).  This laptop has two USB2 ports and one USB3

Just bought a Corsair Voyager USB3 memory stick, wrote 20:04 to it but it will not boot if plugged in to the USB3 port, boots fine if moved to USB2

I have a number of various Linux images installed on an external conventional spinning disk and these images boot fine in the USB3 port

If it wasn't for fact the conventional disk works fine in the USB3 port I'd suspect the connection.

Anyone got any idea what may be the problem?

Geoff

---

### Post by sudodus on 2021-05-30
USB 3 in oldish computers may be kind of experimental and not quite compatible with all hardware.

I have a [similar Toshiba Satellite laptop](http://www.toshiba.se/laptops/satellite-pro/c850/satellite-pro-c850-19w/), and I have better luck, it works well with most USB 3 pendrives also via its USB 3 port. For example, my Corsair Voyager GT 3.0 32 GB works via the Toshiba's USB 3 port. Just to be sure I cloned the current daily Lubuntu iso file [FONT=Courier New]**impish-desktop-amd64.iso**[/FONT] to verify it.

---

### Post by ActionParsnip on 2021-06-01
Just boot it in the USB 2.0 port.... Surely?

---

### Post by Geoff_Lane on 2021-07-18
> **sudodus said:**
> USB 3 in oldish computers may be kind of experimental and not quite compatible with all hardware.



Yes, guess so, we do expect quite a lot and most of the time it works.

Geoff

---

### Post by Geoff_Lane on 2021-07-18
> **ActionParsnip said:**
> Just boot it in the USB 2.0 port.... Surely?

Naturally that is the only option I have, defeats the object a little of the USB3 speed but having said that, once up and working I think the live images mainly run from RAM

Geoff

---

### Post by ActionParsnip on 2021-07-18
If USB 2.0 works.... Use that

---

### Post by ActionParsnip on 2021-07-18
> **Geoff_Lane said:**
> Naturally that is the only option I have, defeats the object a little of the USB3 speed but having said that, once up and working I think the live images mainly run from RAM

Geoff

Not booting USB 3 will leave the port free for external storage devices you want to use. Over time the kernel will use the RAM as disk cache and will hardly touch the USB storage.

---

### Post by Autodave on 2021-07-18
I have a new machine and 5 USB 3.0 drives: all newer.  I have ONE drive though, that will work on any of the USB 3.0 ports except one of them.  All other drives work on that port, but one refuses to.  Go figure.

---

