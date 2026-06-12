---
title: "Dualshock 4 doesn't work in any kernel newer than 3.14"
date: 2015-10-20
forum: Gaming &amp; Leisure
---

### Post by Chris on 2015-10-20
I'm surprised there are not more complaints about this. Maybe nobody uses a Dualshock, I don't know. Or maybe it's just me.

I have spent a whole bunch of time testing the Dualshock 4 connected wirelessly via bluetooth. Kernel 3.14.54 is the last kernel where the Dualshock is functional (the trackpad and motion sensors do not work though). Beginning with kernel 3.15.0 the trackpad works but nothing else on the controller does. I tested all the way to kernel 4.3 and it's still broken.

Has no one else experienced this? Anyone successfully running a 3.15 or newer kernel and a Dualshock 4 via bluetooth?

---

### Post by crastopher on 2015-10-20
I'll be more than happy to try this out.

By chance, what bluetooth adapter are you using?

---

### Post by Chris on 2015-10-20
I'm testing with a generic China Bluetooth "Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)". That device may not be 2.1 bluetooth so that could possibly be an issue (works fine on kernel 3.14 though). I'm also testing a modern Dell laptop (not sure what bluetooth hardware it has but almost certainly 2.1+EDR).

I read on the Gentoo wiki that they recommend using BlueZ at least version 5.14 whereas on Ubuntu I'm only running 4.101. Maybe that's the problem... Hmmm. However, I did test Ubuntu 15.10 and that supposedly has bluez 5.35 or somesuch. It didn't work there either so. Eh....

Just to be sure I retested on all my machines with Ubuntu 15.10 which has BlueZ 5.35 and kernel 4.2.0. Does not work.

To be sure I'm using the "latest everything" I tried testing in Arch Linux. Same result. Trackpad works but nothing else.

It's like being in the Twilight Zone. The hid-sony kernel module has had very active development. How could it have possibly been broken this long without anyone noticing? I must be doing something wrong.

I found the problem in the Linux kernel and sent a patch to the Linux dudes so hopefully this will be fixed in future kernels.

Apparently new DualShock 4's have a slightly different protocol. Either that or there is a firmware update that gets applied when you connect the controller to a PS4 (mine never has).

---

### Post by kreeturez on 2015-12-13
> **Chris said:**
> I found the problem in the Linux kernel and sent a patch to the Linux dudes so hopefully this will be fixed in future kernels.

Apparently new DualShock 4's have a slightly different protocol. Either that or there is a firmware update that gets applied when you connect the controller to a PS4 (mine never has).

Wow, glad I found this: was having the same issue. 

My original DS4 Controller (which came with my PS4) works brilliantly: all my newer (original) ones don't. I just get the equivalent of a continuous left-button-press with all of them. 
None of the new ones have been connected to my PS4 so I'm not sure if it's firmware related. Maybe it's a new Vendor or Product ID?

Could you link to where you found this out? (And maybe to your patch?)

Thanks again!

---

### Post by kreeturez on 2016-01-31
Reportedly fixed as of  kernel version 4.5 (RC1)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1511855](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1511855)

Great news, that.

---

### Post by LifeEnemy on 2016-02-05
I've had that same problem using a PS3 controller connected via usb. Really annoying. At one point I "fixed" it somehow by playing with Steam Big Picture settings, but it recently reared its head again. :(

---

### Post by Ubuntwan on 2016-02-12
I too have a brand new DS4 paperweight for my ubuntu pc...(I bought it too play Wii games in Dolphin, so the accelerometers and gyro's were kind of important too me :(   ) 
On bluetooth only the touchpad works, on USB all buttons and sticks work as well as the trackpad, but no accelerometers or gyro's...
Great to see it is solved. Thank you for finding it, and getting it patched Chris (and others)!
Will patches like these be implemented in earlier ubuntu kernelupdates as well? Given it is patched in kernel 4.5rc1, and my current ubuntu 15.10 is running kernel 4.2, ubuntu 16.04 seems to ship with 4.4, will it take until end of this year (16.10?) before stock ubuntu will update to a >4.5 kernel and we will see the DS 4 working again in a regular install?

kreeturez,
are you willing to connect your new DS4 to your Playstation to see if this possible firmware upgrade solves it? If so, I will try and locate a PS4 to connect mine to and update it to get it working before I get a 4.5 kernel. Or can you no longer connect to a pc after it has been connected to a Playstation? 
cheers,
Ubuntwan

---

### Post by kreeturez on 2016-03-01
> **Ubuntwan said:**
> I too have a brand new DS4 paperweight for my ubuntu pc...(I bought it too play Wii games in Dolphin, so the accelerometers and gyro's were kind of important too me :(   ) On bluetooth only the touchpad works, on USB all buttons and sticks work as well as the trackpad, but no accelerometers or gyro's...Great to see it is solved. Thank you for finding it, and getting it patched Chris (and others)!Will patches like these be implemented in earlier ubuntu kernelupdates as well? Given it is patched in kernel 4.5rc1, and my current ubuntu 15.10 is running kernel 4.2, ubuntu 16.04 seems to ship with 4.4, will it take until end of this year (16.10?) before stock ubuntu will update to a >4.5 kernel and we will see the DS 4 working again in a regular install?kreeturez,are you willing to connect your new DS4 to your Playstation to see if this possible firmware upgrade solves it? If so, I will try and locate a PS4 to connect mine to and update it to get it working before I get a 4.5 kernel. Or can you no longer connect to a pc after it has been connected to a Playstation? cheers,UbuntwanTo test this out, I've been using one of these non-working new controllers on my (firmware-updated) PS4. Last night I tried it on my Ubuntu machine and it had the same issue: I'm guessing controller firmware isn't the problem. (Also these newer controllers must have newer firmware in any case but don't work with Ubuntu - whereas the older ones do...)Looks like updating the kernel is the only way to sort this out. Still, very glad it was submitted and patched (thanks, Chris!)

---

### Post by Ubuntwan on 2016-03-02
Ok, good to know it has nothing to do with connecting to a PS4. Thanks for trying it out.
Hopefully the patch can be installed with backports...
Ubuntwan

YES! just upgraded to Ubuntu 16.10 which has a new enough kernel, and low and behold: The Dualshock 4 works out of the box this time, with motion/tilt and trackpad and everything. The unit did not get much use last year, so hopefully the battery is still good enough. It is happily charging at the moment.
Thanks everybody.
Ubuntwan

---

### Post by oldrocker99 on 2016-10-13
If the problem is solved (and it apparently is), please mark this thread as [SOLVED].

---

### Post by Ubuntwan on 2016-10-14
I tried of course, but it seems these settings are not available to me (which seems related to the forum upgrade)
I will try and manually change the thread title, but it seems I can only change my posts title.
We'll see.

---

