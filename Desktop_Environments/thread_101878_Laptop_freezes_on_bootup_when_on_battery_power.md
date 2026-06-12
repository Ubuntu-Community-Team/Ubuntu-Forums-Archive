---
title: "Laptop freezes on bootup when on battery power"
date: 2005-12-10
forum: Desktop Environments
---

### Post by timelord726 on 2005-12-10
My IBM ThinkPad T22 runs Ubuntu very well, but I can't get past one particular issue. Whenever I boot the laptop without being connected to AC power (running on the battery), it freezes at one particular spot each time. The only workaround I've found is to boot the computer on AC power and then unplug it after it's booted. As you can imagine, this wouldn't be very much fun if I had to boot running on battery and was away from any AC power sources!

This is the part where it stops:

```
* Starting hotplug subsystem...          [ ok ]
* Setting up ALSA card 0...
``` 
Then the system just freezes and I have to hold the power button for five seconds to turn the machine off. Is there anything I can do to make sure it is able to boot while it's running on the battery?

Thanks!

---

### Post by timelord726 on 2005-12-12
Some additional information.  I reformatted my laptop last night for various reasons, and it still does the same thing.  I've narrowed down the cause -- it's my Broadcom wireless card (a Linksys WPC54GS) running via ndiswrapper.  When the card's not in the machine, it boots normally.  Also, to amend my previous post, it now freezes at:

```
* Starting hotplug subsystem...
```

I know what causes it, but I still don't know how to fix it.  Can anyone help me?

---

### Post by greenway on 2005-12-13
Just of the top of my head; try adding "acpi=off" to argument on the kernel line in /boot/grub/menu.lst.

---

### Post by timelord726 on 2005-12-13
Thanks very much for the response!  I shall try it as soon as I get home and back to my laptop.

---

### Post by timelord726 on 2005-12-15
I am in your debt, sir.  I did not expect that to work, but it did!  Thank you so much!

---

