---
title: "Sensor Applet -- temp1"
date: 2009-05-23
forum: General Help
---

### Post by melopsittacus on 2009-05-23
Hi! Sensor Applet displays values temp1, CPU and GPU. I know the meaning of CPU and GPU, however I do not know what "temp1" could be. Maybe some chip on the mobo, like north bridge, or RAM mobules? It has a very suddenly oscillating value (from 30 to 45 degrees) and preferences say that it is connected to libsensor->temp1

---

### Post by hal8000 on 2009-05-23
> **melopsittacus said:**
> Hi! Sensor Applet displays values temp1, CPU and GPU. I know the meaning of CPU and GPU, however I do not know what "temp1" could be. Maybe some chip on the mobo, like north bridge, or RAM mobules? It has a very suddenly oscillating value (from 30 to 45 degrees) and preferences say that it is connected to libsensor->temp1

Temp1 will most likely be an ambient sensor on your motherboard- of which model you forgot to tell us. Not to worry, cosult your motheboard manual to find this out.
You can always rename "temp" to something more meaningful in the configuration file. In ubuntu this is /etc/sources.conf
H8k

---

### Post by khelben1979 on 2009-05-23
Maybe you should try [ksensors]("http://en.wikipedia.org/wiki/Lm_sensors") instead? (see wiki link)

```
sudo apt-get install ksensors
```
to install it with root priviliges.

---

### Post by melopsittacus on 2009-05-24
Hi, thanks for the replies. The motherboard is Asus A8N-E, however I did not find anything about sensors in the manual.

As for ksensors, I did not install it (because it would pull the whole KDE libraries as usual :)), however the application it relies on (lm_sensors), turned out to be quite useful:

```

$ sensors
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +38.0°C

```

This value corresponds to the value reported by temp1. After some googling I found that k8temp-pci-00c3 is the temperature of the CPU. Now the problem of temp1 seems to be solved, but a new question arises: what could the temperature reported as CPU temp be? I begin to doubt that this value is not connected to anything at all, as it seems to constantly stay on 40 C, no matter what the computer is actually doing.

---

