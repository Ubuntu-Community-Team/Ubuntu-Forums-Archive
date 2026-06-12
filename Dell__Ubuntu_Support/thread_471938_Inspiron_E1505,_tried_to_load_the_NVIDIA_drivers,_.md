---
title: "Inspiron E1505, tried to load the NVIDIA drivers, lost X, lost all my function keys"
date: 2007-06-12
forum: Dell  Ubuntu Support
---

### Post by UberIcarus on 2007-06-12
Just got the laptop, and I tried to enable the restricted drivers through restricted driver manager. I lost X, and I was able to do a "sudo dpkg-reconfigure xserver-xorg" and get nv running. Problem now is that my resolution is *much* lower, and I've lost th function keys to enable the wireless card....which is a problem because that's the only way I know how to turn it on, to do a reinstall of the drivers... Is there a dell utility to reinstate the keyboard profile and graphics driver settings?

---

### Post by bunted on 2007-06-12
Did you backup your xorg.conf file before you made all of these changes?

I would revert to a configuration before you had this problem and go from there.

---

### Post by UberIcarus on 2007-06-12
I loaded the old xorg.conf....still doesn't work. Resolution will only go up to 1280x1024, and the function keys still don't work.

---

### Post by UberIcarus on 2007-06-12
Okay, I edited the original xorg.conf file, and I have my good resolution back, however I still do not have the wireless card. As in: It does not show up in ifconfig, or in network manager. running ifup or ifconfig up gets me no device found.

---

### Post by UberIcarus on 2007-06-12
okay, I've tried manually loading the deb packages from the software channel, nothing will restore the nvidia modules. Modprobe just gives me a very very generic error (even with the -v flag) that just tells m it fails to load. Okay so fine, I can go back to the nv drivers....but how the hell do I get my wireless and keyboard function commands back?

---

### Post by UberIcarus on 2007-06-12
SOLVED: for som reason when I installed nvidia-glx from restricted-drivers manager, it did not install the low-latency kernel. I couldn't actually find out what was wrong until I tried to run restriced-drivers manager again as modprobe gives crap for error output. In any event, manually installing the packages for the low latency kernel fixed everything, including my wireless card.

---

