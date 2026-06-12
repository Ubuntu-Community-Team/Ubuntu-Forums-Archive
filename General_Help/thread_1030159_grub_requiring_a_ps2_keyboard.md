---
title: "grub requiring a ps/2 keyboard"
date: 2009-01-04
forum: General Help
---

### Post by Virgofenix on 2009-01-04
I can select items in the grub menu only by using a ps/2 keyboard. Is this normal? Is there a way to use a usb keyboard in grub?

---

### Post by Elfy on 2009-01-04
Yes that's normal. Not sure that there's a way to use a usb keyboard in grub, I keep a PS2/usb adaptor handy.

---

### Post by heindsight on 2009-01-04
That seems a bit strange. I've been using usb keyboards for years and i've never had a problem using one with grub. Perhaps you need to change some setting in your BIOS?

---

### Post by TerryArnott on 2009-01-04
I have seen this issue on some MoBo's.  I am pretty sure it falls back to the bios of the MoBo and whether it will support USB keyboard/mouse independent of the OS.

Many older boards will recognize a USB keyboard at post and allow you to use it to enter the bios, change settings etc, but it then seems to revoke that support and the USB keyboard then won't work until the OS picks it up.  You often see this with a USB keyboard not working when you are in the boot options for XP after a failed start-up, you know the one where you can select boot normally, safe mode, last known good config, etc.

My suggestion would be to check in your BIOS for an option to support USB keyboard, and failing that, check the the MoBo manufacturers website and see if there is a bios update for it that may solve the problem.

A note of caution, the PS2 ports are not buffered and so you should NEVER plug or unplug a PS2 device (mouse or keyboard) while the machine is powered up, as you risk popping the PS2 controller and having a dead keyboard port on your MoBo.  It won't do it every time, but if you keep doing it, you are going to loose the port eventually, it may be the second time you do it, or it may be the hundredth.  Trust me, i found out the hard way and now have a couple of boards here that will ONLY run USB as keyboards.

If you can't solve the problem, your only solution is to stick a cheap PS2 keyboard round the back plugged in all the time and just pull it out when you need it, and keep your main, good USB keyboard on the desk, or go with a PS2 keyboard permanently.

Hope this helps.

T

---

### Post by rbmorse on 2009-01-04
There may be, in your BIOS setup, a setting to enable/disable "support for legacy USB devices" or similar.  Depending on the capabilities of the BIOS, you may need to enable this setting before the BIOS will recognize or control USB interfaced keyboard/mouse. 

Thanks to TerryArnott for reminding that PS/2 ports are not hot pluggable.  Once the PS/2 controller dies it can't be resurected.

---

### Post by Virgofenix on 2009-01-29
Yes, thanks - it was in the BIOS. You nailed the fact that the USB keyboard did allow me to enter the BIOS but not select at grub. Why did I wait three weeks to check back after the first two replies? I've been coping by using a Live CD all the while.

---

