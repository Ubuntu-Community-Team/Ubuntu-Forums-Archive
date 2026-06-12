---
title: "Screen Resolution"
date: 2007-08-02
forum: Dell  Ubuntu Support
---

### Post by jayk121121 on 2007-08-02
I have a Dell XPS 410 N with a 256MB nVidia Geforce 7300LE TurboCache (with Ubuntu preinstalled).  I also bought a Dell 20 inch UltraSharp™ 2007WFP Widescreen Digital Flat Panel from the same page.  At first the highest screen resolution was 800x600.  I installed the nVidia driver with the Restricted Drivers Manager, because this fixed the screen resolution on my laptop.  Now the screen only goes to 1024x768, while it said that the monitor should go to 1680x1050.  Can anyone please tell me how to make the resolution go to that point?

---

### Post by Rocket2DMn on 2007-08-02
You probably need to reconfigure your Xserver (the GUI).
```
sudo dpkg-reconfigure xserver-xorg
```
This will take you through a setup of your hardware, including video driver and screen resolutions.  Use TAB to move around and SPACEBAR to select/enable.  When you get to the resolutions page, enable your monitor's max resolution and everything less.  Then you need to restart X by hitting CTRL+ALT+BACKSPACE.  This will close all GUI apps, so save your work, and you will be taken back to the login screen.  You should then be able to login and set your resolution correctly.

---

### Post by jayk121121 on 2007-08-02
The screen resolution problem is fixed, but now the windows load without borders!  The only other things I changed besides screen resolution is changing the driver from vesa to nvidia and enable frame buffer graphics (not sure sure what that is, but it said it was safe to enable it).  I appreciate any help.

Update: The borders came back after I turned off Desktop Effects.  It does not really matter to me, so I am fine with it as it is now.

---

