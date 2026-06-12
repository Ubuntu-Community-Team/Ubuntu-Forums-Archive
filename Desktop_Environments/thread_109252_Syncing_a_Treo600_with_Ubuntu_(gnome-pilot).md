---
title: "Syncing a Treo600 with Ubuntu (gnome-pilot)"
date: 2005-12-28
forum: Desktop Environments
---

### Post by sola on 2005-12-28
Hi,

I have a problem syncing a Treo600 with an Ubuntu Breezy machine by gnome-pilot (with Evolution). This is an older, Celereon based machine with 512 MB of RAM and USB1.1 ports.

The weird thing is that I have a newer Breezy laptop (P4, 768Mb RAM) which does the sync perfectly. This one has USB2 ports.

I am using the USB2 cable of the Treo600 and the hotsync button on it.

The symptoms:
After I boot the Celeron machine and log into the Gnome desktop, the first sync works - usually (not always). Then I cannot sync again only after a complete reboot of the machine. (log-off & log-in doesn't help, only a complete reboot.)

On the P4 laptop there is no such problem. I can sync the Treo600 any times and works without any problems.

If I start gpilotd from the console and watch its messages, I see warnings about timeouts (although timeout warnings come much faster than the actual timeout period).

Any idea or similar experience?

Thanks,
Andras

---

### Post by Sokraates on 2005-12-28
Do you have some other USB-devices plugged to your box? I could only imagine that maybe Ubuntu looks for your Treo on a certain device (usually ttyUSB1) which is sometimes occupied by another device. this would also explain the reboots, since devices are assigned at system startup.

Take a look at [this](http://ubuntuforums.org/showthread.php?t=77387) thread. There are some commands mentioned. With those you can find out which dievices are used by your Treo when you tried to hotsync. Also you can see, which devices work.

---

### Post by sola on 2005-12-28
Thanks a lot!!!

Reading the thread you sent, I found that I should change the device from /dev/pilot to /dev/ttyUSB1. With this hard-wired setting, it syncs any number of times without any problems. 

God knows why but my laptop works with /dev/pilot and the Celeron machine doesn't.

I checked /dev/pilot on the Celeron machine with "ls - la" and saw that it links it to /dev/ttyUSB0 when it doesn't work and to /dev/ttyUSB1 when it works. So the gnome-pilot daemon recognizes the usb port incorrectly for some reason and tries to link the wrong usb device to /dev/pilot. 

It is lucky that the gnome-pilot control applet allows to manually provide the device so I could enter /dev/tyUSB1.

Thanks again,
Andras

---

