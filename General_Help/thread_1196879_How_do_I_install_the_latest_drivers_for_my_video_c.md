---
title: "How do I install the latest drivers for my video card?"
date: 2009-06-25
forum: General Help
---

### Post by Vikhyath on 2009-06-25
[FONT=Courier New]Hello,
I downloaded the latest drivers for my video adapter in .tar.gz format and want to install it. how do I do it?[/FONT]

---

### Post by aysiu on 2009-06-25
So the current drivers aren't good enough? You've already gone through System > Administration > Hardware Drivers and that doesn't work?

If you absolutely need the latest, forget about the .tar.gz and use Envy:
[http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A)

---

### Post by Vikhyath on 2009-06-25
> **aysiu said:**
> So the current drivers aren't good enough? You've already gone through System > Administration > Hardware Drivers and that doesn't work?

If you absolutely need the latest, forget about the .tar.gz and use Envy:
[http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A)
its not that the current drivers arenot good enoungh ,but its for the solution of [http://ubuntuforums.org/showthread.php?t=1196799](http://ubuntuforums.org/showthread.php?t=1196799)
Also, System > Administration > Hardware Drivers says no proprietary drivers are in use in this system.

---

### Post by del_diablo on 2009-06-25
Then what video card do you have?

---

### Post by Vikhyath on 2009-06-25
intel 82845G/GL

---

### Post by Vikhyath on 2009-06-25
I can't find intel listed in envy :(

---

### Post by Arup on 2009-06-25
Intel drivers are compiled into kernel, you don't neeed any drivers, only xorg-intel is installed in this case.

---

### Post by The-Don on 2009-06-25
I would recommend not installing proprietary drivers - they pwned my system, even with xorg.conf rewrites...never again on my desktop!

ATi for me by the way.

Just leave Ubuntu sort out the drivers for graphics ;)

---

### Post by aysiu on 2009-06-25
> **Arup said:**
> Intel drivers are compiled into kernel, you don't neeed any drivers, only xorg-intel is installed in this case.
Yes, only Nvidia and ATI video cards require driver installation, because the drivers are proprietary and can't be incorporated into the Linux kernel.

The drivers for Intel should already be there. I guess you could try manually upgrading to a new kernel or recompiling the kernel (I've never done that, but someone else here can help you with that).

---

