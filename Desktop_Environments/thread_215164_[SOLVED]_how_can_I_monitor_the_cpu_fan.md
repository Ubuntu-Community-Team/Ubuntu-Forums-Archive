---
title: "[SOLVED] how can I monitor the cpu fan?"
date: 2006-07-13
forum: Desktop Environments
---

### Post by saul_2110 on 2006-07-13
I'm using a laptop Acer 3620 series. I noticed the fan doesn't stops and I'd like monitor it so to see if at least if regulates its speed.
Is there a utility for this?

---

### Post by phansiizwe on 2006-07-13
A combination of the following packages might do the trick:

lm-sensors
libsensors3
sensors-applet

Note, however, that you have to do some configuring on the lm-sensors...

---

### Post by bigken on 2006-07-13
1st monitor it in the bios then use the above answer and compare ;)

---

### Post by phansiizwe on 2006-07-13
bigken,

are you talking about the accuracy/update of the sensors?!

Until posting the previous message, I only used two temperature sensors. After adding the CPU speed, I now noticed that the values do not change that much over time. I'm wondering about the 1.5sec update interval...

---

