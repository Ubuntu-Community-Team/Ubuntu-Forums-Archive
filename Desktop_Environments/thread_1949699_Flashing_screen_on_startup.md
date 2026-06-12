---
title: "Flashing screen on startup"
date: 2012-03-30
forum: Desktop Environments
---

### Post by Ekeout on 2012-03-30
Hi.

This issue affects xubuntu 11.10, Lubuntu of the same build Mint 12 (gnome), but not Kubuntu 11.10.

The issue is: Boot from Live disc: Ok.
Boot to installed OS : Flashing login screen, very hard to see anything.

Boot into recovery mode - 
glxinfo | grep VGA : "VGA compatible controller: ATI Barts Pro [ATI Radeon HD6800 series] (It's a 6850)

glxinfo | grep Vendor: 
with Mint 12: "Error: unable to open displays"
With Lubuntu 11.10: glxinfo not installed, to install..

Grub is set to 640*480 mode. Have tried (via recovery mode) to install xserver-xorg and reconfigured xserver-xorg via dpkg to no avail.

I don't think fglxr is used by default as Lubuntu actually started OK once, just once, and then the fglxr was in the list of restricted drivers that were available. I tried to activate them but the system crashed midway (with dump on screen).

What advice can be given?

---

### Post by Rex Bouwense on 2012-03-30
Need a little more information.  All four of the OS that you tried can boot from a live CD, but apparently you cannot boot with the installed OS.  Is that correct?  What is the installed OS?

---

### Post by Ekeout on 2012-03-31
That's the gist of it, yes. They're ok off their live CDs but once they are installed on the hd and one attempts to boot into them things cease to work as intended: 

The login screen simply flashes very rapidly and the login items are decentered, meaning the image isn't perfectly aligned with the monitor.

I'm running Win 7 on a different partition on the same HD. The grub bootloader looks and works ok. The current Linux system is Lubuntu 11.10.

I've seen this issue described for a number of editions of Linux, but not found a solution. I suppose it may manifest due to slightly different reasons, but the culprit is likely the graphics card and the drivers chosen for it automatically. So how to fix?

---

### Post by Ekeout on 2012-03-31
Turns out that adding the argument nomodeset to the boot line (Default linux boot option in grub - hit 'e' , add argument to end of line) fixed that.

I wonder if there's any way of seeing what graphics driver is in use when there's no Xorg.conf though.

---

