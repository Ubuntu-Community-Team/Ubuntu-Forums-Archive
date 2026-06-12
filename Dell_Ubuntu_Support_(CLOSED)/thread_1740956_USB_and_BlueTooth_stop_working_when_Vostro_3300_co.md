---
title: "USB and BlueTooth stop working when Vostro 3300 comes out of suspend on Maverick"
date: 2011-04-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by hitbyambulance on 2011-04-27
OK, I'm able to (barely) tolerate the external monitor flickering through the VGA output, but this is really annoying. USB and Bluetooth functionality completely disappear - as if the modules failed to reload - after resuming from suspend on Maverick. 

Repro:

1) Boot into Ubuntu 10.10 on Vostro 3300
2) Close laptop lid
3) Wait 30 seconds
4) Open laptop lid
5) Attempt to 
   a) plug in a USB peripheral or
   b) attempt to establish a Bluetooth connection

Actual results:
No USB peripheral or Bluetooth connection will function.

Expected results:
Normal USB and Bluetooth operation.


I expect I'll have to write a bug up and submit to Launchpad, but I'm not sure which modules need to be bugged. I attempted ubuntu-bug bluez, but the screen sat on "Collecting problem information" and never displayed the "Send problem report to the developers?" dialog.

---

### Post by ryannathans on 2011-05-10
I'm on 11.04 64bit and the damn thing wont even detect bluetooth at all!

Dell Vostro 3300

What should I do? Checked bug reports but no solutions help me...

---

### Post by hitbyambulance on 2011-05-10
> **hitbyambulance said:**
> OK, I'm able to (barely) tolerate the external monitor flickering through the VGA output, but this is really annoying. USB and Bluetooth functionality completely disappear - as if the modules failed to reload - after resuming from suspend on Maverick. 

Repro:

1) Boot into Ubuntu 10.10 on Vostro 3300
2) Close laptop lid
3) Wait 30 seconds
4) Open laptop lid
5) Attempt to 
   a) plug in a USB peripheral or
   b) attempt to establish a Bluetooth connection

Actual results:
No USB peripheral or Bluetooth connection will function.

Expected results:
Normal USB and Bluetooth operation.


I expect I'll have to write a bug up and submit to Launchpad, but I'm not sure which modules need to be bugged. I attempted ubuntu-bug bluez, but the screen sat on "Collecting problem information" and never displayed the "Send problem report to the developers?" dialog.

just a follow-up that upgrading to Natty (11.04) appears to have fixed this issue.

---

