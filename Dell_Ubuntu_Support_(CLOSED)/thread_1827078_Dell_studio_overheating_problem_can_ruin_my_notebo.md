---
title: "Dell studio overheating problem can ruin my notebook"
date: 2011-08-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by realpsygnosis on 2011-08-17
I'm starting to get very bored of ubuntu, linux and of my Dell studio 1537 =_=
It seems that only windows works -.-
I've installed ubunto 11.04 everything works, except for a glinch of the graphic card (ATI mobility HD 3450 and catalyst 11.7) that every time I move a window seems like the animation is laggy and opengl is activated becuse with```
 glxinfo | grep direct
``` I have```
 direct rendering: Yes
```but this is not my BIG problem....

I start to notice that the fan doesn't work, or better they are really slow and the notebook is really HOT...
so I installed xsensor and use the command sudo sensors-detect
I reboot
and the only sensor I see are:
acpi
coretemp
coretemp
and in acpi there are temp1 temp2 temp3
really too generic, isn't it?
the main problem is theat I have 50°C on temp1 and 70°C on coretemp
TOO HOT my notebook can really fuse with this temp and I can't use it well because it's too hot to touch the keyboard...
I think that the problem is the ACPI/DSDT but I don't know how to patch it...and I can't find a pre-patched DSDT for my laptopt...I don't know what to do except return to windows...
Plase help me
thanks in advance

EDIT:
I've tested on win with cpu-temp I have 49°C in idle, on linux I have 61°C with xsensors (cpu temp)
Kernel is 2.6.38-10-generic
and with the system in idle without any app open I have cpu1 9.8% and cpu2 8.2%
the strange thing is that the coretemp seems stopped at 61°C sometime it low on 60°C and come back to 61°C

---

### Post by realpsygnosis on 2011-08-18
no one know something on this problem?

---

### Post by realpsygnosis on 2011-08-19
bump

---

