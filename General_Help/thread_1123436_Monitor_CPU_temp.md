---
title: "Monitor CPU temp"
date: 2009-04-12
forum: General Help
---

### Post by bossa on 2009-04-12
Hi All
Could someone please tell me which CPU temp monitor is correct ? ( Running AM2 x2 4200) I have LM-sensors which reads my CPU at 27c Hardware sensor monitor that says CPU temp 27c>ACPI/THRM 40c, CPU scaling monitor shows 40c emfreq applet shows 40c but was showing 27c before I changed my cooler.
Which one should I monitor? I can adjust the speed of the fan on my cooler which can vary the temp that is read by the lm-sensors...so I guess thats the one that should concern me.
Any advice appreciated.

---

### Post by 0cton on 2009-04-12
I think 40 is normal for teh CPU
27 is to less IMHO (unless udnerclocked and watercooled or smth_)

---

### Post by Malta paul on 2009-04-12
I am using Lm-sensors which are displayed in the top panel. I monitor my CPU fan speed as well as temp. also monitor CPU load. I find that these will vary with the program load. My video card give the highest temp. but stays well within limits.
I know this does not answer your question, just thought you might like the info. ;)

---

### Post by bossa on 2009-04-12
> **0cton said:**
> I think 40 is normal for teh CPU
27 is to less IMHO (unless udnerclocked and watercooled or smth_)

Hi Octon
The temp changes from 27c to 28c in LM-sensors (X-sensors)  when I slow the fan (Zalman Fanmate) in hardware sensor the core temps  are Core0 25c and Core1 32c CPU 30c cpu 40c(ACPI/THRM),I'm confused..so you reckon 40c is normal? I have CPU scaling at automatic

---

### Post by lovinglinux on 2009-04-12
You should compare those readings from lm-sensors with those from the BIOS.

From my experience, these sensors are not precise and might need some adjustments depending on your hardware. For example, some of my sensor were displaying negative temperatures when I first installed.

---

### Post by bossa on 2009-04-12
> **lovinglinux said:**
> You should compare those readings from lm-sensors with those from the BIOS.

From my experience, these sensors are not precise and might need some adjustments depending on your hardware. For example, some of my sensor were displaying negative temperatures when I first installed.

I just checked in the bios and the CPU Temp is 25c Sys temp 30c. X-sensors says CPU 30c MB 21c temp 3 (?) 27-28 -30c. Hardware monitor is reading about the same except the CPU THRM which is always 40c.

---

