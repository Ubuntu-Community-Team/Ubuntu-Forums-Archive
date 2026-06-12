---
title: "Things freeze: firefox, sudo, logout.."
date: 2009-03-21
forum: General Help
---

### Post by Flare777 on 2009-03-21
I've got a weird recurring problem that I can't blame on anything specific and so am having trouble searching for info about.

Randomly sometimes around 0-2 times a day, I'm multitasking and then Firefox won't load a page, and freezes over if I click on it. I then find that Pidgin has lost its connection and won't finish reconnecting. I then try and sudo a tool or two for info, but any sudo command hangs before asking for a password and ignores Ctrl-C interrupts. In a despair, I save my work on things like Gedit and Eclipse and then Log Out, only to find the screen hangs on a black screen with "* Reloading system log daemon" (paraphrased) and never makes it back to the login screen.

I don't know where to look for errors when this happens, please help!

---

### Post by prshah on 2009-03-21
> **Flare777 said:**
> 
Randomly sometimes around 0-2 times a day, I'm multitasking and then Firefox won't load a page

a) I'd suggest running a memtest (available as an option from the GRUB startup menu); if that passes

b) remake your swap memory ```
sudo swapoff -a
sudo mkswap /dev/sdXY
sudo swapon -a
``` Replace /dev/sdXY with your swap partition id.

c) Use the live CD for a while and see if the problems occur

d) Check the internal fans in the system; if they are not working, overheating can also cause such problems.

---

