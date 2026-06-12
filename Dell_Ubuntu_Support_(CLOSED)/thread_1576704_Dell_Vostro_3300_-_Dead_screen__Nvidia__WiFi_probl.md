---
title: "Dell Vostro 3300 - Dead screen / Nvidia / WiFi problems"
date: 2010-09-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by aalex85 on 2010-09-17
Hi there, never wrote in the forum before, but as I didn't find nothing clear about this I decided to write down my experience.

I recently received my Vostro 3300 (amazing machine!):
- CPU intel core i5-520M
- graphic card Nvidia GeForce 310M
- Dell Bluetooth 365 + Dell Wireless 1501
- default OS Windows 7 Home Premium (32Bit)

I unpacked, started windows, tried Win7 for some minutes and then finally resided the windows partition for installing Ubuntu...
CD in, boot, install set-up, reboot, log-in, everything seems fine... then I installed the restricted driver for the wlan and the graphic card, reboot and... **blank screen after grub**...

Blank screen, system dead with every kind of input, only thing to do is fore shutdown with long pression on power button.

I thought "ok, that's the Nvidia driver, always messy". Re-installed and as first time the system boot. Then I activate the wireless support, do a system update and reboot......... dead screen again! Mmh....... so first time was not due to the Nvidia driver...

Well, I spent almost a week trying to figure out the problem/a solution and then it just came to me accidentally: **I TURNED OFF THE WIFI HARDWARE SWITCH** then the boot got me to the log-in, then I reactivated the WiFi and no problem.
No much of an explanation for this, but it works! Just boring to turn it on/off all the time.

PS: I tried once more to install the Nvidia drivers after that but I ended up with a black screen (confirming the problem with the EDID of the LCD panel), but I was able to start from grub adding "nomodeset" instead of "quiet splash" and get into a X reconfiguration minimal system so I purged the Nvidia drivers (sudo apt-get remove nvidia-current) and restored my /etc/X11/ folder (carefully backed-up at first boot).

Now I have an operative system but without official Nvidia drivers, not that bad, I will wait for next month's release to see if things changes.

PPS: all other things work fine after install (webcam, esata, sd reader, keyboard multimedia keys).

:D

---

