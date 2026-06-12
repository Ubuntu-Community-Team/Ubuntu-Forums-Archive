---
title: "Monitor CPU, GPU, etc. temperatures while gaming..."
date: 2008-01-23
forum: Gaming &amp; Leisure
---

### Post by DasCrushinator on 2008-01-23
Is there a way to do this?  I would like to have a program that either records all of my temps every second to a file or show me what the peak temps were for each piece of hardware after a gaming session.

---

### Post by Melcar on 2008-01-23
Good question.  I know of several sensor monitoring apps. out there, but have yet to find one that makes logs.  As for video cards, I think the nvidia proprietary drivers provide temp. monitoring, but I know for a fact that fglrx does not provide this feature yet.

---

### Post by DasCrushinator on 2008-01-24
> **Melcar said:**
> Good question.  I know of several sensor monitoring apps. out there, but have yet to find one that makes logs.  As for video cards, I think the nvidia proprietary drivers provide temp. monitoring, but I know for a fact that fglrx does not provide this feature yet.

Well, I use nvidia-settings and conky to monitor temps, but I don't think it creates log files.

---

### Post by bryanbankester on 2008-01-24
[http://packages.ubuntu.com/gutsy/gnome/computertemp](http://packages.ubuntu.com/gutsy/gnome/computertemp)

This can log CPU temps.

---

### Post by nille on 2008-01-24
If you have found a program that reports your current temp you can always write a short shell-script. Try **acpi -V** and see if it gives you any good output, or check out **lm-sensors**.

I have used this script, but it will probably not work for you, but can perhaps give you some ideas:

```
#!/bin/sh
mv thermal1.log thermal1.log.old
mv thermal2.log thermal2.log.old
while true;
    do acpi -t | awk '/Thermal 1/{print $4}' >> thermal1.log
    acpi -t | awk '/Thermal 2/{print $4}' >> thermal2.log
    sleep 10
done
```

---

