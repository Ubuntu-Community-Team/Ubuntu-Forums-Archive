---
title: "Can't change speed with CPU Frequency Scaling Monitor applet"
date: 2005-08-28
forum: Desktop Environments
---

### Post by Panthios on 2005-08-28
Hi.

I have read that it is possible to change the CPU speed with a single click on the applet. But it does not work. It's on auto all the time.

Do I have to change something to change the CPU scaling manual?

Best regards

---

### Post by pmjdebruijn on 2005-08-28
Hi,

Well does your CPU even support CPU frequency scaling? This is a feature which is generally ment for use on Laptops.

If you don't know please type this in the Terminal: 'cat /proc/cpuinfo', and paste it in here.

Regards,
Pascal de Bruijn

---

### Post by Panthios on 2005-08-28
[QUOTE=pmjdebruijn]Hi,

Well does your CPU even support CPU frequency scaling? This is a feature which is generally ment for use on Laptops.

If you don't know please type this in the Terminal: 'cat /proc/cpuinfo', and paste it in here.

Regards,
Pascal de Bruijn[/QUOTE]

I am on a laptop, and it does work (auto - as I wrote, scaling up and down every time I use my laptop.)

I figured it out why I couldnt manually set it to like 1000mhz, but it works now.

$ chmod +s /usr/bin/cpufreq-selector


 :wink:

---

