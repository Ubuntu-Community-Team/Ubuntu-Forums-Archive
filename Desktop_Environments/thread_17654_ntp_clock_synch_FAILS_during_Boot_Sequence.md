---
title: "ntp clock synch FAILS during Boot Sequence"
date: 2005-03-01
forum: Desktop Environments
---

### Post by iminj on 2005-03-01
I have warty installed on an old IBM Thinkpad laptop with network connection via a PCMCIA nic.

I've noticed that the Boot Sequence for "Starting PCMCIA Services" is approx. 8 or 9 steps AFTER the failed ntp clock synchronization to ubuntu's server. This probably means the attempt to connect occurs BEFORE my nic has been activated.

Is there a reliable method to modify the order of these commands ? If anyone knows, please share the information.

Thanks !

-iminj

---

### Post by cka on 2005-03-02
I have it setup to sync to the ntp server twice...  once in rcS (this is the one that fails on my machine), and once in rc2 (it syncs after GDM starts because at that point my PPPoE connection is fully made and the DNS works.)  You should be able to copy S??ntpdate out of /etc/rcS.d into /etc/rc2.d and give it an appropriate boot sequence number (preferrably one of the final items, so around 60 or 70 so it would be /etc/rc2.d/S60ntpdate

---

### Post by iminj on 2005-03-02
[QUOTE=cka]I have it setup to sync to the ntp server twice...  once in rcS (this is the one that fails on my machine), and once in rc2 (it syncs after GDM starts because at that point my PPPoE connection is fully made and the DNS works.)  You should be able to copy S??ntpdate out of /etc/rcS.d into /etc/rc2.d and give it an appropriate boot sequence number (preferrably one of the final items, so around 60 or 70 so it would be /etc/rc2.d/S60ntpdate[/QUOTE]

THANKS !! It worked.

I copied /etc/rcS.d/S51ntpdate to /etc/rc2.d/ and renamed the copied file S60ntpdate. 
Now, when I boot, there are 2 attempts to ntpdate. The first one (my original) fails, but the 2nd attempt is "OK". 

.... which begs a question ... What harm is there in removing the 1st attempt (S51ntpdate) from rcS.d ?

-iminj

---

### Post by cka on 2005-03-02
There shouldn't be any harm in it. 

Besides, if there is you can just boot to a recovery console and ln -s /etc/init.d/ntpdate /etc/rcS.d/Sxxntpdate or however that command works.

---

### Post by iminj on 2005-03-02
Works perfectly !

I removed the 1st instance of ntpdate, and powered down my laptop. On the subsequent bootup, there is only 1 attempt to connect to the ntp server. It happens AFTER my nic is loaded, and it connects.

cka ..thanks very much for walking me thru this. The terrific ubuntu community comes thru again .. 

-iminj

---

