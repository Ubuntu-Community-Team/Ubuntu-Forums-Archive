---
title: "Weird SDL behaviour with i915 drivers"
date: 2006-07-15
forum: Desktop Environments
---

### Post by gspr on 2006-07-15
Hi.

I have an Intel 855GM in my laptop, and I used to have a problem with DRI. For that reason, I didn't care wether I ran the new i915 or the old i830 kernel module for the card. After I had given up on DRI, I kept the i915 driver. It soon turned out that there is a strange issue with the i915 driver and SDL performance (I'm talking 2D here). An SDL application, such as OpenTTD, would run horribly choppy at 1400x1050, and barely playable at 800x600 using the i915 driver. With i830, everything was more than smooth at 1400x1050. I thus stuck with the older i830 kernel module, and forgot all about this.

Recently I decided to give DRI another try, and it finally works, but only with the i915 module. So, I have a problem - either I can have DRI and 3D acceleration, and broken 2D SDL performance with i915, or I can have no DRI or 3D acceleration but great 2D SDL performance with i830. The latter is much more important for me, since I'm not a gaming person, but still, it would be very nice to be able to utilize what little this laptop is capable of.

Has anyone experienced anything similar? Any known solutions? What in the world could be causing this? The i915 driver should be a lot better than i830, right? And with the former now giving me DRI, SDL should be glad, right?

I've also tried with SDL applications other than OpenTTD. One thing I tried with was a little SDL program I made last month. For debugging resons while developing the program, I had it notify me every iteration it missed a drawing deadline. With the i830 driver, this only happened if I started moving the window around or something like that, it NEVER happened with regular usage. Also, CPU usage was around 30%-50% with the CPU clocked down to 600 MHz. Now, with i915? EVERY iteration misses its drawing deadline, by 1-20 ms (depending on the rest of the system's CPU load), even with the system running on a full 1700 MHz.

Any ideas, anybody? In this state, DRI and 3D acceleration are not of much use to me. I'm in much more need of 2D SDL performance than "finally" being able to play tuxracer smoothly...

Some info:
o I'm running an up to date Dapper.
o Kernel version is 2.6.15-26-386.
o Laptop has an Intel 855GM card.
o VideoRam is set to 65536 in the Xorg config. Anything less than 32 megs would not give me DRI.
o Resolution is 1400x1050.

---

### Post by gspr on 2006-07-20
Bump...

---

