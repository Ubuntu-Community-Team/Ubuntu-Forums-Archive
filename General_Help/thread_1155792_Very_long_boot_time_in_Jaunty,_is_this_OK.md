---
title: "Very long boot time in Jaunty, is this OK?"
date: 2009-05-11
forum: General Help
---

### Post by iyepb0 on 2009-05-11
Hello people,

I need your experties in this one.
Well , i just installing the new JJ ubuntu.
But, i got stunning by the "fast boot" that this JJ do. It stuck for about 3 minute in booting process.
Stuck in the "Loading Hardware Drivers" line...

This is dmesg line with some unordinary line -see for timing in bracket-:

> [   12.500111] Clocksource tsc unstable (delta = -162196340 ns)
[   12.733075] Synaptics Touchpad, model: 1, fw: 6.2, id: 0xa0b1, caps: 0xa04713/0x20040a
[   12.765745] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input7
[   14.184182] iwl3945: Radio Frequency Kill Switch is On:
[   14.184186] Kill switch must be turned off for wireless networking to work.
[  190.461016] lp0: using parport0 (interrupt-driven).
[  190.519197] Adding 570268k swap on /dev/sda11.  Priority:-1 extents:1 across:570268k
[  190.533154] EXT4 FS on sda10, internal journal on sda10:8
[  190.765477] EXT4-fs: barriers enabled

Will somebody share their experties with me...

Thank you 
and keep 
Open Source Your Mind

Regards,
iyep

---

### Post by Peter09 on 2009-05-11
Have you a printer attached to a parallel port? Try a boot with it disconnected.

---

### Post by iyepb0 on 2009-05-11
> **Peter09 said:**
> Have you a printer attached to a parallel port? Try a boot with it disconnected.

No, i dont have a printer... and in my laptop there was no parallel port :confused:

---

### Post by cybrsaylr on 2009-05-11
I'm using 64bit JJ and it boots up in 55 seconds on my laptop.

---

### Post by Denestria on 2009-05-11
> [ 14.184182] iwl3945: Radio Frequency Kill Switch is On:
[ 14.184186] Kill switch must be turned off for wireless networking to work.


When it finally does boot your wireless network isn't working?  Check if your laptop has a network kill switch and it is turned off.  If it is all ready off then there may be a driver problem.

---

### Post by iyepb0 on 2009-05-12
> **cybrsaylr said:**
> I'm using 64bit JJ and it boots up in 55 seconds on my laptop.

Wish it happen to me... :(

> **Denestria said:**
> When it finally does boot your wireless network isn't working?  Check if your laptop has a network kill switch and it is turned off.  If it is all ready off then there may be a driver problem.

The wireless switch was turned off at boot and working normally after boot.
So, perhaps it was a driver problem.


I found that i am not alone with this problem. Have a look here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/316405](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/316405)
[https://lists.ubuntu.com/archives/universe-bugs/2009-April/074636.html](https://lists.ubuntu.com/archives/universe-bugs/2009-April/074636.html)
And i have the same type tv tuner card
But, solution that exist is to blacklist a module that will make my tv card not working...any other way?

Thank You Everyone

---

### Post by Denestria on 2009-05-12
Looks like they have all ready fixed it, don't know how long it will be before it is released as an update though.  You can blacklist the module,  the card won't work but you can boot normally until then.

```
gksu /etc/modprobe.d/blacklist.conf
```

To the end of the file add: 
blacklist saa7134

Then when the fix is released to the repositories all you have to do is edit the file again and remove that line.

---

### Post by petrus4 on 2009-05-12
> **iyepb0 said:**
> Hello people,

I need your experties in this one.
Well , i just installing the new JJ ubuntu.
But, i got stunning by the "fast boot" that this JJ do. It stuck for about 3 minute in booting process.
Stuck in the "Loading Hardware Drivers" line...

I'm running Ubuntu 8.04 I think it is; can't remember the name of it, and I have the same problem.

Personally I suspect it is HALd, although I admit I'm not entirely sure.  Network config seems to have problems as well.

---

### Post by iyepb0 on 2009-05-18
Solve it with compile the 2.6.29.1 kernel with this tutorial [here]("http://ubuntuforums.org/showthread.php?t=311158")

Thank you everyone

---

