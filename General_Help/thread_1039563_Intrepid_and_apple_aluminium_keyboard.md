---
title: "Intrepid and apple aluminium keyboard"
date: 2009-01-14
forum: General Help
---

### Post by Chang on 2009-01-14
Hi, I am trying to use an apple aluminium keyboard in a PC with Ubuntu intrepid, dual booting with windows xp. Can't use the keyboard up and down keys at the Grub menu. Read somewhere that hid-apple drivers need to be installed? If this is the solution, could you please let me know where to get the drivers and how to install them. Thanks.

---

### Post by robobot on 2009-01-14
Installing the hid-apple drivers won't fix your GRUB problem, as those aren't loaded until Linux starts.

I had the same problem with a different keyboard, and I found two different solutions for it. The first one is to use a USB-to-PS2 adapter (they usually come with USB keyboards and mice). The other one is to check in your BIOS and see if you can enable USB keyboard support there.

I'm not sure if either of these will work for you, but they're worth a try.

---

### Post by Chang on 2009-01-15
Thanks response. USB keyboard is enabled in BIOS. Keyboard and mouse are connected to a Belkin USB KVM switch, so USB-PS2 adapter won't work. Tried a colleague's Logitech Flat USB keyboard and that worked with the Grub menu at start up. As a matter of interest, where do you get hid-apple drivers and how to you install them?

---

### Post by Chemical Imbalance on 2009-05-08
I'm also having issues with this keyboard.  

I have an Asus board with an Award BIOS that requires the DEL key to enter setup.  
The problem is, there is no DEL (forward delete) key on this keyboard!
GRUB menu also does not work.

I've read on various google searches that fn + delete(the apple ~backspace key) is equivalent to del, but still no luck entering BIOS.

I wish Apple would've kept in mind PC users in making their keyboards...

I hate to have to buy another keyboard just to enter my BIOS and GRUB menus!:cry:






Anyone know something I don't?

---

### Post by Chemical Imbalance on 2009-05-08
I just bought a numeric keypad to get into and navigate my BIOS today.  Works great, so problem solved for me at least.

Also, it seems turning on legacy usb support in the BIOS lets me navigate my grub menu with my apple keyboard
--though I still need my new GE usb keypad to get into the bios (need the DEL key on it).

---

