---
title: "Monitor goes to sleep during startup and won't wake up"
date: 2005-03-03
forum: Desktop Environments
---

### Post by drew_t on 2005-03-03
I installed Ubuntu on a Windows XP system that has an Nvidia GeForce2 GTS AGP video card.  When I boot into Ubuntu, the machine goes into the normal startup sequence, then, after the "starting GNOME display manager" line appears, the screen goes blank for a bit.  If I have a CRT monitor hooked up to the system, I hear a "click" from the monitor (which I associate with the monitor going into sleep mode); after a few seconds, the little spinning icon pops onto the screen, then the screen which asks for the login appears, and all is well.

If, on the other hand, I have the system connected to my SVA VR-15A LCD monitor, after the screen goes blank, the monitor generates a "no signal" message, and, after a few seconds, goes into sleep mode, and stays in sleep mode.  The system isn't locking up; I can blindly type in my user name and password, and get the music that plays when the desktop appears.

I had this problem after the initial installation; I continued to have it after adding all the additional repositories and updating everything, and after installing the Nvidia driver; and I also have it when running the Ubuntu live CD.

I have browsed this forum, and seen some suggestions that the wrong horizontal or vertical settings are being used, and that the LCD is going into the sleep mode as a defensive measure.  Is this what I am experiencing, or is the blanking of the screen when the GNOME display manager starts up a "legitimate" trigger for the monitor to go into sleep mode (recall that the CRT monitor appears to do the same thing), and then some unknown problem keeps it from waking up?  Is it possible to configure the display manager to *not* blank the screen while it is starting up? 

Any help/suggestions appreciated.  Note: I am basically a Linux newbie.

---

### Post by doitashimashite on 2005-03-03
I'm not sure what happens here. Could you try to use the combination CTRL-ALT-BACKSPACE (resets the X-server) when the screen blanks?

Did you switch monitors after the installation, or did you install Ubuntu with this monitor attached?

---

### Post by drew_t on 2005-03-03
I did the installation with the LCD monitor connected.

Hitting control-alt-backspace does not make the monitor wake up.  (The "bongo drum" noise plays, and I can again blindly type in my user name and password.)

---

### Post by drew_t on 2005-03-03
One more thing: I've just borrowed a Dell E151FP LCD monitor, and  am not having the same problem with it.

---

### Post by doitashimashite on 2005-03-04
Coincidentally, I have the exact same situation on one of the installations I did.
I spent 15 minutes trying this and that, and though I couldn't find a cause, what I did find was a workaround, and that is simply booting from a previous kernel.

At the grub menu, the default kernel is:

Ubuntu, kernel 2.6.8.1-5-386

Select the other one:

Ubuntu, kernel 2.6.8.1-3-386

and (at least in my case) the graphics will come up again.

If it helps for you too, you can change /boot/grub/menu.lst in order to make this permanent: in the line

default             0

the 0 (zero) should be changed into 2.

Though it's just a workaround, I hope it will work for you.

---

### Post by drew_t on 2005-03-04
Thanks for the suggestion, but unfortunately it didn't work for me.

---

