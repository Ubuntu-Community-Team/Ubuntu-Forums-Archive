---
title: "Vostro 1710 CPU fan won't turn off!"
date: 2009-09-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by shlape on 2009-09-22
I originally posted this thread in the Hardware & Laptops section but have more-recently found this Dell support forum, so here I go again.

I don't mind that the fans are working, but the CPUs are under 30C and the fans are still going. It's keeping the CPU's safe but overuse of a critical piece of equipment such as cooling fans has me concerned. Can anyone help?  Does anyone think the Dell-supplied version of ubuntu would fix this?

My original post follows...

> **shlape said:**
> I have a Dell Vostro 1710 which I recently installed v9.04 onto. All went well except, in comparison to the last distro I used, the CPU fan spins up often at low temperatures.

I have installed lm-sensors. I ran sensor-detect. Running 'sensors' on the command line gives:

coretemp-isa-0000
Adapter: ISA adapter
Core 0: +29.0°C (high = +100.0°C, crit = +100.0°C)

coretemp-isa-0001
Adapter: ISA adapter
Core 1: +29.0°C (high = +100.0°C, crit = +100.0°C) 

The 'coretemp' module exists and has been modprobe'd in.

I considered altering the /etc/sensors.conf file but could not find any convincing help online or from the comments within said file.

Can anyone help??

---

