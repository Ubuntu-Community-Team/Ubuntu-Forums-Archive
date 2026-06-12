---
title: "Dell Vostro 3500 Wireless Problem"
date: 2010-11-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by cozski on 2010-11-22
Hello

I've installed Ubuntu 10.10 on my works laptop and now have the option to boot into Windows 7 or Ubuntu. I cant seem to see any wireless networks when booting into Ubuntu. It works fine with Windows. Any thoughts/suggestions/ideas welcomed.

Thanks in advance, regards, Coz.

---

### Post by mikewhatever on 2010-11-23
Dell usually uses Broadcom wireless cards which don't work out of the box in Ubuntu for the lack of driver. To install the driver, connect an ethernet cable, then open System->Admin->Drivers.
In case you get an error when installing, check out the link below for a fix.
[http://www.ubuntumini.com/2010/10/broadcom-wireless-driver-fix-in.html](http://www.ubuntumini.com/2010/10/broadcom-wireless-driver-fix-in.html)

---

### Post by cozski on 2010-11-24
Thanks... I'll give that a whirl as soon as I can get to an Ethernet Connection and let you know.

---

### Post by mauricio.dev on 2011-01-24
Just for your information, I've done the same installation and I'm on a wireless card nightmare.
The STA driver that ships with ubuntu has latency problems (lowering your speed to 10%).
Recompiling the driver didn't do any good.
I've also tried to follow a guide to install bcm80211 module (that seems to be the open source alternative). It actually works. But from time to time I still have latency (much softer) issues. At least it's not as huge as to lower my traffic speed.
I'm trying ndiswrapper now. I don't know if this is going to work.
Wish me luck

---

### Post by mauricio.dev on 2011-01-24
Great news.
ndiswrapper worked great!
I had to find the windows xp driver. I didn't find on dell's site so I risked using one found on [this blog]("http://laptop-driver.blogspot.com/2010/12/dell-vostro-3500-windows-xp-driver.html"). 
Well, the good thing is: it's working. I've used ndisgtk interface and I had to blacklist every ubuntu module possible on /etc/modprobe.d/blacklist.conf

```
#trying to make ndiswrapper work
blacklist b43
blacklist b43legacy
blacklist bcmwl
blacklist wl

```

And that's it. It's working perfectly now. I didn't test much, but the latency problems are gone.
The tests I did were: pinging my router (witch gave me 200ms sometimes before the windows driver) and playing a fps online (witch was nearly impossible).
I hope it helps!

---

### Post by affus56 on 2011-03-04
ya its working fine but when i was trying  install ns-allinone-2.34, I did the following steps its showing b43 required
Do you want to continue [Y/n]? y
Setting up firmware-b43-installer (4.150.10.5-4) ...
Not supported low-power chip with PCI id 14e4:4315!
Aborting.
dpkg: error processing firmware-b43-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 firmware-b43-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
what i need to do now 
please can u help me out

---

### Post by affus56 on 2011-03-04
I followed the below site for installing ns-allinone-2.34 in  my dell vostro 3550. It showed the above message error 

[http://getch.wordpress.com/2010/10/25/installing-network-simulator-in-ubuntu10-10](http://getch.wordpress.com/2010/10/25/installing-network-simulator-in-ubuntu10-10)

Please help me to solve the problem.

Its really urgent to me

thank you

---

