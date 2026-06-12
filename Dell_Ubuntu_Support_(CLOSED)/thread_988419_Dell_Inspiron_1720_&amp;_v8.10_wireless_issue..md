---
title: "Dell Inspiron 1720 &amp; v8.10 wireless issue."
date: 2008-11-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Synaptyc on 2008-11-20
Hey gang,

Let me start by saying I had 8.04 working with wireless perfectly.
Once I upgraded to 8.10 wireless stopped working.
I know this is a known issue with 8.10 and a lot of systems, but I wanted to bring attention to my particular setup and problem.

I used ndiswrapper + ndisgtk with 8.04 and all was well.
8.10 seems to come with it's own driver that will work with my "Dell 1505 Wireless 802.11N" card (Broadcom 4328 chipset).
I did the following to try to resolve my "wirelessness".

After upgrading to 8.10 I removed everything "ndis" and rebooted.
Upon reboot I went to the "Hardware Drivers" icon on the right side of the tool bar.
It displayed a driver named "WL" and it was lit-up green and currently in use.
I still had no wireless activity and their was no wireless setting in the network manager.

After reading this link ---> [http://ubuntuforums.org/showthread.php?p=6093691#post6093691](http://ubuntuforums.org/showthread.php?p=6093691#post6093691)
I simply did the following:
*** I opened the Terminal and typed:
```
sudo rmmod b44
sudo rmmod ssb
sudo rmmod wl
sudo modprobe wl
sudo modprobe ssb
sudo modprobe b44
```

And... WHAM! My wifi light came on.
I went back to the Network Manager and could now select my wireless network.
Once I entered my WPA "passphrase" I was connected.
I started downloading the updates and after 2-3 minutes wifi stopped working and the updates stalled.
I brought up the web browser and couldn't surf online.

Here's what I want to do:
1) fix the problem and get wifi working constantly with this "WL" driver that comes with 8.10
2) remove (disable) the "WL" driver and get NDISWRAPPER + NDISGTK working again.

Note: I have wiped my HDD and installed 8.10 fresh from the CD and I get the same result.
I tried installing the latest ndiswrapper (v1.52 i think, from the repositories via ethernet)
along with ndisgtk. I can install the XP drivers for my "1505 Wireless N" (Broadcom 4328 chipset) adapter.
NDISGTK says the driver is installed and the hardware is present, but when I press the "configure network" button I get an error.

ANY TIPS OR HELP TO GET ME ONLINE USING WIRELESS ONLY???

~Syn

---

### Post by PinkFloyd102489 on 2008-11-20
Dont use ndiswrapper. Use the wl driver. It works much better and gives full 54Mb speed.

```
sudo apt-get install linux-restricted-modules-`uname -r`
```


Run that command (note the grave symboles). Blacklist the ndiswrapper module in /etc/modprobe.d/blacklist and then load the wl driver. It's a little bit wonky at startup so add this to /etc/rc.local:

```

#!/bin/bash

sudo rmmod ssb
sudo rmmod b44
sudo rmmod wl
sudo modprobe wl
sudo modprobe ssb
sudo modprobe b44

```

---

### Post by dizcrypt on 2008-11-21
@Synaptyc:
There is no need in ndiswrapper for 8.04. In fact wl works perfectly for it, but it was broken in 8.10.

---

### Post by Synaptyc on 2008-11-21
UPDATE: After getting my WiFi working using the "WL" driver via 'Hardware Drivers' I setup my router to be OPEN instead of WPA security. Now it stays connected and has a pretty good data transfer rate. Now I just need to get WPA or WEP or some type of security between my router and all my computers!
Thnx for the help!!!

---

