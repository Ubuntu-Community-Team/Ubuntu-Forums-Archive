---
title: "Dell Inspiron n5010 Bluetooth Issue"
date: 2010-11-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ma1 on 2010-11-29
Hi All,


I have just installed Ubuntu 10.10 on my Dell Inspiron n5010 Laptop, but the bluetooth is not working. I have tried all bluetooth packages available in Ubuntu Software Center, but no success.

lsusb output:

[SIZE=2][B][COLOR=Black]Bus 002 Device 003: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
[/COLOR][/B][COLOR=Black]
[/COLOR][/SIZE] hcitool scan output:

[SIZE=2][B]Device is not available: No such device
[/B][SIZE=1]

[SIZE=2]Is this a device driver problem (Broadcom devices always have issues)?

Is there anyway to fix it?[/SIZE] 


[/SIZE]Regards,[/SIZE]

---

### Post by KImre on 2010-12-07
Does everything else work?
Somebody said wireless lan don't work with broadcom-wl or ndiswrapper.

---

### Post by werty2010 on 2011-01-23
im facing exacly the same problem
if anyone solved it could you post a link for the rest of us?

---

### Post by wijit on 2011-09-26
Me the same. Since this thread is a bit old, it might be sorted out. If anyone can guide me to a solution it will be more than appreciated.

---

### Post by O.elgedawy on 2011-11-26
i booted in to my Windows 7 installation system and removed and re-installed the BT driver again
and that fixed for me.

i think the driver maybe updated the BT firmware or something like that.

---

