---
title: "Sticky Cursor"
date: 2005-12-06
forum: Desktop Environments
---

### Post by Sef on 2005-12-06
The cursor sticks in a corner and even if i move it with my USB Logictech Value Optical Mouse, it tries to go back to the corner, which it does as soon as i stop moving my mouse.  It has worked fine with Feather Linux and Vector Linux.

Computer: Dell 4100, 700 MHz, 128 Ram

What can I do to fix this, so I can use Ubuntu?

---

### Post by 23meg on 2005-12-06
What type of mouse is it, in terms of connection method? Please post the InputDevice section of your xorg.conf file that corresponds to your mouse.

---

### Post by Sef on 2005-12-06
It's a USB mouse, but I have a ps/2 adapter.  I have tried that too, but still the same problem.

How do I get to the InputDevice Section?

---

### Post by 23meg on 2005-12-06
Since it may be an interference problem with another input controller (a touchpad if it's a laptop, for example), it's actually best if you post your whole xorg.conf file.  Open the file in gedit ```
gedit /etc/X11/xorg.conf
``` paste its contents on this site : [http://sh.nu/p](http://sh.nu/p) and post the url here. Or post the file as an attachment.

---

### Post by migueljacq on 2005-12-06
Yep. I had this problem too, and it was due to the touchpad going a bit crazy. The usb mouse couldn't override it, would keep sliding across the screen.

Evidently your options are to carefully clean the touchpad, or turn the touchpad off in BIOS and stick to an external mouse. I chose the latter.

---

### Post by Sef on 2005-12-08
Shutting off the touchpad worked for me.  Thank you all for your suggestions.  It is nice to have Ubuntu on my laptop.

---

