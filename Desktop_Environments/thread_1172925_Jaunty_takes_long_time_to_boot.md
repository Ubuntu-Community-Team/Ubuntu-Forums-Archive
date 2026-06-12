---
title: "Jaunty takes long time to boot"
date: 2009-05-29
forum: Desktop Environments
---

### Post by pvpkiran on 2009-05-29
Hi ,
   I hav recently upgraded to jaunty.Ever since then , loading takes a long time.

Actually at some point during boooting, it gives a message
"Loading kernel..... modules" 
and stalls for a long time.

Pls help


Thank U

---

### Post by Pengwyn44 on 2009-05-30
Did you load 9.04 as an upgrade program? If so I suggest that you do a clean install from a 9.04 CD. I have noticed that 9.04 loads much more quickly than 8.04 that I was using previously.

---

### Post by pvpkiran on 2009-08-18
Hi all,
   with respect to the above problem, 
I hav taken the booting logs from /var/log/dmesg. In which one of the part reads

 [   42.812470] type=1505 audit(1250572968.900:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2279
[   42.833772] type=1505 audit(1250572968.921:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2283
[  218.070123] Bluetooth: BNEP (Ethernet Emulation) ver 1.3


This is where it is taking a lot of time. It is taking 218 sec for loading Bluetooth . And also a lot of time on other programs as well.

Can someone tell me why is it taking so much time. 



Thanks

---

### Post by XubuRoxMySox on 2009-08-18
I can't say why it's taking so long. My jaunty boots up very quickly - much faster than Intrepid did, but I did a fresh install instead of an upgrade if that makes a difference (and I really suspect that it does).

If you don't use bluetooth, you can tell Jaunty not to bother loading it (System tools > Services, uncheck bluetooth). In fact you can un-check any services you don't need to have loaded at startup and that should speed things up for you.

-Robin

---

### Post by wojox on 2009-08-18
+1 @ dixiedancer's idea
You can also google "speed up jaunty boot time" and find some more little tweaks.

---

