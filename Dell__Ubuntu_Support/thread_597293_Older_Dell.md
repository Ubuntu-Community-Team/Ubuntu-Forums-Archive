---
title: "Older Dell"
date: 2007-10-30
forum: Dell  Ubuntu Support
---

### Post by Diebloem on 2007-10-30
Greetings

After hearing a lot about Linux, and trying to understand the principle differences to MS products, I am very keen to use Ubuntu. I have read that this OS is not as hungry on hardware resources as MS – all the more reason to try on an older system.

Use is a GX110 OptiPlex Desktop, 1G CPU (P3), 384 RAM. 
Worked well with XP pro even with only 256 RAM, albeit not a rocket.

Installation worked well, it understandably took longer than the 25 min mentioned. 

Reboot – black screen.

Is it naive to expect this system to work ?

Many thanks for your comments.

Kind regards

---

### Post by ajgreeny on 2007-10-30
Try Ctrl+Alt+F1 to see if you get a terminal.  If so, login with your username and password, (remember if you do this properly there is no feedback, you will just be logged in).

Now type ```
sudo dpkg-reconfigure xserver-xorg
``` and press enter and accept all the defaults until you get to the video card part where you will need to chose the appropriate driver for your card, so you need to know what it is.  At the end type ```
sudo reboot
```hit enter, and with luck you will get to a gui when it comes back.

If you still have problems come back again.

---

### Post by Mike Armstrong on 2007-10-30
It may be more comforting to re-install in safe graphics mode then when you have a system up and running (though only in the centre part of the screen ), you can then do as in the above post though I would select "vesa" as the initial card selection then work through to set your resolution. When you get to the three options for graphics the middle one of which is "medium" select this and reconfirm the resolution and 60hz refresh for the laptop screen. Just esc or accept all the other confusing defaults. Worked for my old Inspiron 8000 with the same amount of ram as yours.

---

### Post by Mud.Knee.Havoc on 2007-11-07
> **Diebloem said:**
> 
Reboot – black screen.
Is it naive to expect this system to work ?


It sounds like the same problem my relatively new Inspiron 1501 has loading most Linux distros.  I have to add "acpi=off" and "nolapic" to the end of the line in grub that boots the kernel.

You might as well give it a shot - it's not going to do anything bad if the system already won't boot. :D  If you don't know how to do this, you'll need to use a live CD or boot into "recovery mode" and edit /boot/grub/menu.lst

If you scroll down, you'll see the grub menu laid out, more or less.

---

