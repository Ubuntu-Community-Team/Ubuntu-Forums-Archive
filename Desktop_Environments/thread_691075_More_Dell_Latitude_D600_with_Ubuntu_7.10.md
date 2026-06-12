---
title: "More Dell Latitude D600 with Ubuntu 7.10"
date: 2008-02-08
forum: Desktop Environments
---

### Post by pumahalen on 2008-02-08
It was a bit of a disappointment after he easy installation to see that thr 7.10 is tougher on the hardware than XP, i expected it to be the other way around.

Cpu scales down to 600 most of the time, but that is still not enough. Worse is that internet browsing sets the fan on full speed after about a minute.

Then there is the battery. Quite a lot of D600-users got a brand new battery from Dell last year, and I was used to about 3 hrs work from the capacity i had when I decided to go for a dual boot. Feisty stated that the battery capacity was about 30 % at the point of installation, and working time was less than 30 min. To my suprise XP  was of the same opinion when I booted back to check what could be wrong. 

I could well be that my battery experienced a rapid decline in the week before the installation, I did not check that on the day of installation. But what I think is that it is a matter of calibration, some low-level driver adjustments that has gone off the mark. There is no reason why XP should have re-adjusted its calculations on capacity, unless:
1. The battery went over the edge without me noticing (might be possible :) ).
2. Low-level driver adjustments gives results in wrong data coming back to the OS.

Maybe this piece of HW is not meant for Feisty, such things happens ...  :confused:

---

### Post by tcommbee on 2008-02-08
what does gnome-power-statistics say? combined with some kernels my amd turion literally worked like an electrical shortcut - about 35W! If you should also see a very high consumption, you probably have no working power managment in your kernel (i only ever used ubuntu 8 alpha on my laptop). a friend of mine has much longer battery life with his intel thinkpad under ubuntu 8 compared to 7.10 but this must not necessarily apply to your case.

---

