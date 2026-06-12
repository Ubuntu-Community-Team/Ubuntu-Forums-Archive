---
title: "Bluetooth problem"
date: 2010-05-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bilalsana on 2010-05-26
hi
i have dell inspiron 1564 and i am running lucid. bluetooth is not working, i ran linux mint from a live cd and bluetooth worked perfectly. However, in ubuntu if i run the bluetooth applet and press turn on nothing happens!

---

### Post by Kai Summers on 2010-05-26
This is currently a known problem with most newer dells (Same problem here with my Inspirion Variant). I think they are currently compiling a driver that will solve the problem but I can't see it being released anytime soon, perhaps in the next 3-4 months.

---

### Post by louij on 2010-05-29
Me too have this problem. So we are going to wait that long to make out bluetooth works? Do you think does it work if we push Dell to release the driver soon?

---

### Post by maxideci on 2010-05-29
I am having the same problem, but Bluetooth works perfect, when I boot lucid using live CD, So I guess there is some problem with the installation. I upgraded from 9.10 to 10.4. It never worked with 9.10 and its continuing the same way.

Any idea how and what steps to take to debug the problem ?

"uname -a 
Linux T-D 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux"

"hcitool dev
Devices:
	hci0	00:22:5F:97:20:A0"

Its Dell studio 1555 with Dell Computer Corp. Wireless 370 Bluetooth Mini-card.

Thanks, 
Cheers!!

---

### Post by dtl on 2010-07-18
Hi everybody, I had the same problem on my Samsung N-150. Solved it by uninstalling the gnome bluetooth and/or blueman. Then I found bluez-tools for Karmic on the web,installed it as well as Kbluetooth. Now it works perfectly. Maybe it's a clumsy way of doing it but untill the Lucid Gnome package is fixed I'm happy. Hope this helps somebody, :p

---

