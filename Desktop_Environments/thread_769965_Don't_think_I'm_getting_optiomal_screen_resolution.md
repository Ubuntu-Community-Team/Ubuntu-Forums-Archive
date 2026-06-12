---
title: "Don't think I'm getting optiomal screen resolution"
date: 2008-04-27
forum: Desktop Environments
---

### Post by websquad on 2008-04-27
I'm a newbe having just installed my first Linux (Ubuntu 8.04) about three hours ago.

During the boot process, I get the following displayed on my LCD panel:

[CENTER]**Input Signal Out of Range**
**Change Settings to 1680 x 1050 - 60Hz**[/CENTER]

Based on the font and graphics, the message appears to come from my HP w22 monitor.  It appears for 1 - 2 seconds almost immediately after the power is on, and then following the BIOS splash screen (in this case, "Compaq").  The second times it appears for about 7 or 8 seconds (alas, not timed with a stopwatch).

Am I getting full resolution?  Is there an interface similar to Windows Properties > Settings > Screen resolution?

---

### Post by Demorgon on 2008-04-27
System -> Preferences -> Screen Resolution

---

### Post by irifan on 2008-04-27
run sudo displayconfig-gtk in a terminal window to configure your monitor and graphics card.

If your monitor is not listed here, please go to the manufactures homepage to get the horizontal an vertical range there.

---

### Post by tormod on 2008-04-27
If this appears during boot and before the login window, the screen resolution tools are not relevant. They configure the Xorg server, which is started a few seconds before  you see the graphical login window.

Do you see the grub menu (after BIOS is done, before Linux is booting)? Do you see usplash (the Ubuntu splash screen with the progress bar)?

---

### Post by websquad on 2008-04-27
Apparently Umbuto "knows" something of my monitor, because when I ran [FONT="Fixedsys"]sudo displayconfig-gtk[/FONT] it indicated that my monitor was set for 1680x1050 and 60Hz.

When booting, I get the following:
1. Graphics notice (previously mentioned)
2. OEM Splash Screen (Compaq)
3. Grub screen
4. Starting Up message
5. Graphics notice
6. Login/password screen

The whole process is extremely fast.

A little OT, but can I do away with the userid/password?  I'm the only user of this machine, and really don't need any security, which apparently can be easily overridden.

Back on-topic, the graphics card is MSI P/N 8962-120 ... that's all I can get from visual inspection of the device.  When I ran "display config" it indicated it was an ATI card, but had no device driver installed.  Is this something I should be concerned with?

---

### Post by tormod on 2008-04-27
If you don't get the usplash (not sure what you mean with number 4 above) you can try to modify the grub kernel line (take away "splash") and see if you still get the notice. usplash sets up the screen resolution as well and it can get it wrong. Check /etc/usplash.conf as well.

For the userid/password thing, yes it's possible. Google for it, but spell Ubuntu correctly.

---

### Post by tormod on 2008-04-27
To identify your graphic card, type: **lspci -nn|grep VGA**

---

