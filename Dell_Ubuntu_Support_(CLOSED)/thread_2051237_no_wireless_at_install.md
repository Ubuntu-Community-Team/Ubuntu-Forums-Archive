---
title: "no wireless at install"
date: 2012-09-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by DOS Chuck on 2012-09-01
I read a couple of posts here about losing wireless support after upgrading but I'm having problems during the initial installation.
I have a Dell Inspiron 1501 I am trying to install Edubuntu 12.04 on. I boot live first of all to connect online but I get a message on the "network" icon stating I need a firmware update. I HAVE installed this very same disk onto a second HDD on my desktop, which uses a wireless network card, with NO problems whatsoever.
I have tried a few, different versions of Linux on this laptop with the SAME problem.
Any help on getting wireless connectivity DURING installation?
Thanks in advance.

---

### Post by DOS Chuck on 2012-09-01
DOH.....nevermind. I think I found it.

---

### Post by 2F4U on 2012-09-01
The desktop certainly has a different network card than the laptop. In any case, if you still have a problem, you should at the least post the model of the network card.

---

### Post by fauhid on 2012-09-01
problem with hardware switch try turning it on.

---

### Post by DOS Chuck on 2012-09-01
The wireless works fine in Windows XP (which I want to get rid of and install Edubuntu). According to "Device Manager", this laptop has a Dell (Broadcom) Wireless 1390 WLAN Mini-card.

If I boot off of a LiveCD of Tails 0.11, the wireless works fine. ANY other flavor of Linux (Ubuntu, Zorin, NetRunner, openSUSE)and I get the firmware message and it flat refuses to install. I had NO problems installing Edubuntu on an external 80GB HDD connected to my desktop. It recognized the wireless card without a problem.

And, to fauhid, just where would this hardware switch be on a laptop card. I have a TP-Link TL-WN951N PCI wireless adapter I am using on my desktop that has NO switch. Neither did the Netgear cards I used before it.

---

### Post by DOS Chuck on 2012-09-03
Ok, I got Edubuntu to install but I still have no wireless connectivity. As for a "hardware switch", the ONLY thing I can find is pressing "Fn" and "F2" on the keyboard which is SUPPOSED to turn it on or off. It does NOTHING. I opened up the back of the laptop, found the wireless adapter and checked to make sure it was properly seated. It is.
Now, I tried a D-Link DWL-122 Wireless USB adapter and got a different problem. THIS adapter shows nearby wireless signals to connect to. If I try to connect to my router, it asks for my passkey but the "connect" button is grayed out. I can't select it. 
I've tried "sudo modprobe b43", it doesn't work. NOTHING I have found on this board has worked....yet. Now that I know that a USB wireless adapter ALMOST works, I still have hope of connecting. Why is the connection dialog limited? It's almost as if I am logged in as a "guest", which I'm not.
Any suggestions?

---

### Post by DOS Chuck on 2012-09-04
FINALLY! Everything works. I tried ONCE again a couple of fixes I found here (manually installing B43 firmware files)and, THIS time, it worked. The Broadcom wireless adapter works and it connects like normal.

Thanks for your help.

---

