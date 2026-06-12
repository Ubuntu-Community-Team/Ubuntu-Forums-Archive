---
title: "computertemp applet question"
date: 2008-07-12
forum: Desktop Environments
---

### Post by pofigster on 2008-07-12
So, I recently installed a new heatsink and a GPU with a Zalmann fan and I have become curious as to how cool my computer is (it's really quiet so I wanted to make sure it was staying cool).

I installed the computertemp applet for the Gnome panel and the lm-sensors package to make it work.  But now I'm confused - it displays hwmon0(*) where * is a number between 1 and 4.  I have no idea though which of these is a CPU temp, which is GPU and which is motherboard.

Additionally, the temperatures being reported are 20+ degrees (F) cooler than the room the computer is in - is that just a motherboard issue?  The computer is air cooled so it cannot be that much cooler than the room it is in.

---

### Post by jim_p on 2008-07-13
If you run "sensors", you will be shown 4 different temperature displays.
#1 is most likely your motherboard's
#2 is your cpu's, although it may be a bit wrong
...

Mine says ```
temp1:       +49.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = transistor
temp2:       +28.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermal diode
temp3:        -2.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = transistor
cpu0_vid:   +0.000 V

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +34.0°C  (crit = +85.0°C)                  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +34.0°C  (crit = +85.0°C)
```
The display shown next to temp2 is wrong, and the correct ones are the ones under coretemp-isa-000x. I dont know why, I suppose it is a different sensor measuring the same thing wrongly or a bug. If your applet can read from the coretemp module, make it display that temp.

---

### Post by Master Chief on 2008-07-13
Ever checked your hard disk temperature?  If not do a [COLOR="Red"]df[/COLOR] to get the device path (mine is /dev/sda1/) and enter:

```
sudo hddtemp /dev/yourdevice
```

Why?  Because your hard disk might be adding too much heat, and coolers are cheap, and will eventually save you from running into trouble ;)

---

