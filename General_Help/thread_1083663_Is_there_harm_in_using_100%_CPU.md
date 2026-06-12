---
title: "Is there harm in using 100% CPU?"
date: 2009-03-01
forum: General Help
---

### Post by rettie on 2009-03-01
Hello everyone! This is probably a stupid question, but here it is!

My Compaq desktop has a Silicon Integrated Systems (SiS) graphics card which is rubbish. I had Ubuntu 8.10 on it, but every once in a while vector-ish lines would pop up all over the screen like a spiderweb. I downgraded to 8.04 in case a more stable Ubuntu would help, and tried different monitors, but I'm sure the problem was the "sis" driver specified in my xorg.conf.

I changed this to "vesa" and it's all good, except now the CPU is being used heavily, usually 100% when watching a film or moving windows around. What will having the CPU like this all the time do to my desktop? On my laptop I'd hear the fan kicking in and the battery would probably die in 15 minutes, but the desktop just sits there quietly, showing 100% CPU load. Is this just gonna overheat and burn out, I'm worried!

Any help would be appreciated and thanks in advance,

Alex

---

### Post by avrilrox on 2009-03-01
I've had my laptop CPU at 100% for hours playing games and nothing happened. It should be fine. Of course, make sure it does not get too hot.

---

### Post by 3rdalbum on 2009-03-01
It's perfectly safe for the CPU to run at 100% capacity for however long you wish. As long as you've got sufficient airflow to assist the CPU cooler, then you will be fine.

Modern CPUs have what's called a "thermal diode"; essentially it's a temperature sensor. The lm-sensors package in Linux can display the information from this sensor. The motherboard is constantly reading the data from this sensor, and if the temperature gets too high, the CPU is immediately turned off. When Linux is reading the sensor and detects that it's getting too high, it will safely turn off the computer before it gets to the automatic-killswitch.

---

### Post by avrilrox on 2009-03-01
> **3rdalbum said:**
> It's perfectly safe for the CPU to run at 100% capacity for however long you wish. As long as you've got sufficient airflow to assist the CPU cooler, then you will be fine.

Modern CPUs have what's called a "thermal diode"; essentially it's a temperature sensor. The lm-sensors package in Linux can display the information from this sensor. The motherboard is constantly reading the data from this sensor, and if the temperature gets too high, the CPU is immediately turned off. When Linux is reading the sensor and detects that it's getting too high, it will safely turn off the computer before it gets to the automatic-killswitch.

Agreed.

You could also add some applets to your Gnome Desktop so that you can keep an eye on the temperatures.

---

