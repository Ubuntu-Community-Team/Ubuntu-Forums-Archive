---
title: "restricted ATI display driver"
date: 2008-08-08
forum: Desktop Environments
---

### Post by space4monkeys on 2008-08-08
After installing the ATI display driver I had to reboot Ubuntu and got black screen. The resolution seems to be to high for my 15 inch monitor. I can run OS just in safe boot. I tried to fix this with reconfiguring the Xserver (sudo dpkg-reconfigure xserver-xorg), but it is just asking me about my keyboard...

How can I change the resolution, after I enable new driver in safe boot and reboot the sistem. It had to be in text mode. Because I can not see anything and had to use CTRL+ALT+F1 to get into the text mode.

---

### Post by Vorian Grey on 2008-08-08
If you persist in dpkg-reconfigure xserver-xorg it will ask you about your video card and driver. If nothing else works, choose vesa. That will at least get your screen back up. 

Then try Envy, found in the repos. It will download and install the  proper driver for your card.

---

### Post by space4monkeys on 2008-08-08
Even if I persist in dpkg-reconfigure xserver-xorg it doesnt ask me about my video card, driver or to change resolution. It just put me back to text mode.
I already found and install the driver, but I cant  get the resolution down. If Envy can get my resolution right, I'll try it.

---

### Post by InfinityCircuit on 2008-08-08
Please try adding the following to the end of Section "Screen"

DefaultDepth 16

It is a known issue that ATI restricted drivers do not export the correct default depth to X.  This may be your issue.

---

### Post by space4monkeys on 2008-08-08
I tried installing the driver with envy to. I reboot and again got the black screen. I tried with sudo dpkg-reconfigure xserver-xorg and it again asked me some keyboard question... and then it put me back to text mode and said: "xserver-xorg post inst warning: overwriting possibly-costumised configuration backup" or something like that.
I used "sudo cp /etc/x11/xorg.conf/etc/x11/xorg.conf_backup" and again tried with sudo dpkg-reconfigure xserver-xorg, but no luck with fixing the resolution.

---

### Post by space4monkeys on 2008-08-08
> **InfinityCircuit said:**
> Please try adding the following to the end of Section "Screen"

DefaultDepth 16

It is a known issue that ATI restricted drivers do not export the correct default depth to X.  This may be your issue.

Where can I find the file?

---

