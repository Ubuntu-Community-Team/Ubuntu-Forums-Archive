---
title: "System Monitor Garbled"
date: 2008-08-03
forum: Desktop Environments
---

### Post by eyal_allweil on 2008-08-03
Ever since I upgraded to Hardy, my Gnome System Monitor appears garbled when I open it. I'm attaching a screenshot; has anyone encountered this behavior? Any ideas on why it's happening or how to fix it?

---

### Post by S29K on 2008-09-08
I have the same problem and can't figure it out either....anyone?

---

### Post by overdrank on 2008-09-08
> **S29K said:**
> I have the same problem and can't figure it out either....anyone?

Hi and what is the model of the graphics card? Have you tried to use the command ```
gksu displayconfig-gtk
``` and set the driver and resolution there. Also if that fails you can use the xfix option when booting into recovery mode.

---

### Post by eyal_allweil on 2008-09-09
displayconfig shows ATI Radeon (fglrx). The top part shows "vesa - generic vesa compliant video cards", and the bottom part shows "ati - Mach8, Mach32, Mach64 ..."

What does each pane represent? Is the top one the default, and the bottom the fallback? Would it help if I posted my xorg.conf?

Thanks-
Eyal

---

### Post by overdrank on 2008-09-09
> **eyal_allweil said:**
> displayconfig shows ATI Radeon (fglrx). The top part shows "vesa - generic vesa compliant video cards", and the bottom part shows "ati - Mach8, Mach32, Mach64 ..."

What does each pane represent? Is the top one the default, and the bottom the fallback? Would it help if I posted my xorg.conf?

Thanks-
Eyal

HI and if vesa is shown on the top portion of the graphics card tab then that is the driver in use. What is the model of the graphics card and have you tried to install the drivers located under system, administration, hardware drivers?

---

### Post by S29K on 2008-09-09
I'm not near the machine right now so I can't try the command you suggested but it doesn't strike me as the solution as the ONLY app that is garbled is the gnome-system-monitor....everything else looks the way it should.

I'll try it when I get to that machine though and report on the results.

---

### Post by eyal_allweil on 2008-09-09
Hi! I'm so glad this thread has come to life!

I didn't have any drivers under System->Adminstration->Hardware Drivers - it said, "No proprietary drivers are in use on this system". I tried changing driver using *gksu displayconfig-gtk* - I tried *ati* and *radeon* - but they caused my screen to black out when I choose the *Test* option.

Any ideas?

---

### Post by overdrank on 2008-09-09
S29K and eyal_allweil I am merely offering suggestions to help with your issues. I do not know what is the issue but was just suggesting the drivers may have some issues as with Hardy the xorg has changed.
 eyal_allweil again what is the model of the graphics card if there is no drivers in the hardware manager then your may have a older ATI card that the driver should come with Ubuntu.

---

