---
title: "My screen beomes blank"
date: 2006-01-15
forum: General Help
---

### Post by ranatanveer on 2006-01-15
i have installed now the ubuntu linux...but my screen is blank...
what could i do
could anyone help me
regards
Rana Tanveer
Linux Student

---

### Post by louisgag on 2006-01-15
Could you add more details?

-Did the install finish clean?
-When is it blanK? RIght after bios?
-Ubuntu 5.10 I guess?
-Does it write anything on the screen?

Try pressing ctrl+alt+(F1 or F2 or F....)
does it bring you to a new commandline?

---

### Post by pianoboy3333 on 2006-01-15
Do you have an ATI card? ex: Radeon X- series

---

### Post by overload2 on 2006-01-15
Don't laugh but I'm using an old Compaq Presario 4505 Pentium 166 MMX.  I am using the motherboard video card since it doesn't take an AGP connection and I don't have a video card that can fit this old ass motherboard.  I have completed the install, rebooted and finished the install.  Then once the Ubuntu banner comes up it starts to load the modules the screen goes blank.  I don't know if I can use the "alt f1-f4" keys because I can't see anything but the computer is still running.  I've press "alt f2" and hit "enter" and typed my username and password the computer thinks for a bit but still know screen.  I've tried rebooting from the command line but that doesn't work.  Does anyone and any ideas or a similar problem?

---

### Post by pianoboy3333 on 2006-01-16
So you can see the command line? In the command line type:

> sudo dpkg-reconfigure xserver-xorg 

Then do:

> sudo nano /etc/X11/xorg.conf 

scroll down to the device section and reply with that info.

---

