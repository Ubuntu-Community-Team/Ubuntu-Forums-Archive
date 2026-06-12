---
title: "[SOLVED] Latitude D830: USB not working after suspend"
date: 2008-06-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mindhaq on 2008-06-10
Hello,

I'm running Hardy x64 on a Latitude D830, which is normally docked to port replicator.

When I wake up from suspend, none of the USB ports are working. No power (as it seems), and no devices working.

lsusb -v just hangs and is not displaying anything.

I'm not sure when this started, probably after some of the more recent Kernel updates. I am certain this worked before.

Concerning power management, the only thing I changed was enabling laptop mode, and letting it handle harddisk powermanagement to get rid of that harddrive-eating problem.

Any hints on how to get my USB working again after suspend?

---

### Post by ethoxyethaan on 2008-06-11
hello mindhaq, 

sorry i cant help you => :(

but. since your using the Dell latitude D830 (and i am aswell) i have a question.

is your Graphics card working? (the restricted drivers). because i cant get mine to work on the 32 bit platform.

(sorry for the topic hijack)

---

### Post by mindhaq on 2008-06-11
> **ethoxyethaan said:**
> is your Graphics card working? (the restricted drivers). because i cant get mine to work on the 32 bit platform.

I never tried 32bit Ubuntu on this laptop.

But the internal Nvidia Quadro NVS 140m worked out of the box - with some inconveniences in twin view, but no lock ups or anything. I'm using the restricted drivers with compiz and all enabled.


Suspend and hibernate it is what bothers me the most. It's really a pity that this is not working as it should.

---

### Post by mindhaq on 2008-06-11
The suspend / USB problem is solved in the next kernel update. I installed 2.6.24-19 via Hardy proposed [as stated on another thread]("http://ubuntuforums.org/showpost.php?p=5151528&postcount=15"), and this works again now.

---

