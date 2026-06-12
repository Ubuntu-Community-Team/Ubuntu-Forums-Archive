---
title: "Dell inspron 6400 wireless driver problem on switch to 10.04"
date: 2010-05-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by g0rt on 2010-05-13
I'm new to Ubuntu and when I installed ver 10.04 it can't connect to the internet. I don't think the driver is installed can anyone help? tell me what info I should also post.

---

### Post by efflandt on 2010-06-05
In Hardware Drivers, the Broadcom STA driver worked with the BCM4311 in 9.10 and earlier Ubuntu versions, but rather weakly on mine.  I couldn't even tell if that worked in 10.04 because I could not get a signal.  So I used automatically supported USB wireless.  Not sure if Broadcom B43 works any better, which is also offered by Hardware Drivers.  Note that Broadcom B43 and STA are mutually exclusive (activating one deactivates the other).

I had to use **nomodeset** (or **radeon.modeset=0**) kernel boot parameter on mine with ATI X1300 video due to boot graphic issues with the new kernel mode setting driver.

---

