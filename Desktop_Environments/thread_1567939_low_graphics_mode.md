---
title: "low graphics mode"
date: 2010-09-04
forum: Desktop Environments
---

### Post by Keith Fox on 2010-09-04
For some reason after updating, somewhere my system is messed up where my 3d acceleration doesn't work.  I found a workaround though, I can get it to work when I reboot, and manually select my OS at the grub2 menu by pressing enter.  It doesn't work all the time this way, but most the time it does allow 3d acceleration to work almost normal. if I let the grub2 timer count down to auto select it will never be 3d accelerated, and prompts me it's going to run in low-graphics mode and I'm given an option to Restart X.
Ok that's one part of it...
Now with my workaround say I got 3d acceleration to work, when I go to System > Preferences > Appearance : and for Visual Effects I select "Normal" (was on none). it will apply fine, until I reboot it gets set back to none.
So I'm having to manually put everything back (graphics) every time I boot, this is a horrible bug.

Then onto another aspect of this wonderful update.  all my letters and numbers on the keyboard are normal, except when I use control and ALT, they don't seem to be mapped correctly because I can't use any of my Keyboard Shortcuts.

---

### Post by Keith Fox on 2010-09-04
nobody else is having these problems also?

---

### Post by 3Miro on 2010-09-04
If you have ATI or NVIDIA card and you are using the proprietary driver, then I would go to System -> Admin -> Hardware Drivers, remove the driver, reboot, then install the driver again.

I have had this problem once, some time ago, on 9.10 (I think) and this is how I fixed it.

---

### Post by Keith Fox on 2010-09-05
thank you for the graphics help.  I don't know how or why this worked, but I removed the recommended driver (for Nvidia) and rebooted, worked fine without it.  I'm going to try to install and reboot again to see if it will go back to junk or still be fixed. thank you

---

### Post by Keith Fox on 2010-09-05
Yeah with the newest version it seems to not work properly.  I was better off without it. Although they do recommend older Nvidia driver versions, I'll try those until I hit a good one, if not I'll just do without nvidia's driver because it works fine without one.

---

### Post by Keith Fox on 2010-09-05
I'm sorry but I spoke too soon, it's hit or miss everytime no matter what driver version I'm using. I tried again without proprietary driver and it did the same thing. It's just a matter of chance it works properly. Pressing enter at grub2 menu doesn't change any chances

---

### Post by Keith Fox on 2010-09-06
As for the keyboard mapping being laid out incorrect: I figured to make a test in the keyboard shortcuts and my problem lies with the ALT keys being mapped wrong. Left ALT is mapped as "Mod5" whatever that means, and right ALT is mapped to "Multi key". the keyboard settings in preferences are set to USA, and defaults.
i think this problem arose around when I installed a program called logkeys. It runs in the background and creates a logfile of all keys pressed, for security purposes. I'm not sure exactly what I should do about remapping the alt keys.. anybody?

---

### Post by ellgor on 2010-09-06
Hi,

For some reason nvidia doesn't get loaded in correctly, hence the hit and miss affair, I found this guide that got mine working great:

1) Download Newest Nvidia drivers from their website
2) Open module blacklist as admin:

sudo gedit /etc/modprobe.d/blacklist.conf
3) Add these lines and save: 

blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv
4) Uninstall any previously installed Nvidia drivers: 

sudo apt-get --purge remove nvidia-*
5) Reboot your computer
6) When an error message pops up saying that Ubuntu cannot load Nvidia drivers, choose Exit to terminal (Exit to console)
7) Login and cd to the directory where you saved your file
 Install drivers

sudo sh NVIDIA-Linux-x86_64-195.36.24-pkg2.run (or whichever package you have, be precise as errors will result in "no such file"
8) Follow the onscreen guide from Nvidia and when done
9) Start GDM

sudo service gdm start

Regards, Ellgor.

---

### Post by Keith Fox on 2010-09-07
thank you

---

### Post by wookienz on 2011-07-21
awesome thanks.

---

