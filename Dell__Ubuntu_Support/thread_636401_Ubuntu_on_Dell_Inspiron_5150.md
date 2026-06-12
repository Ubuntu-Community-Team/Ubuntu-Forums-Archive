---
title: "Ubuntu on Dell Inspiron 5150"
date: 2007-12-09
forum: Dell  Ubuntu Support
---

### Post by veroni on 2007-12-09
Hi there

I tried to install Ubuntu 7.04 on Dell laptop using Wubi (Windows XP already installed). 
However after installation my laptop power off on its own. Any idea what might be the problem or if any one have had similar problems.

Cheers,
Me

---

### Post by kool_kat_os on 2007-12-14
Does this happen frequently or did it happen only once?

---

### Post by John Matrix on 2007-12-30
The issue is discussed in many places, and at great length here:
[http://ubuntuforums.org/showthread.php?t=186003](http://ubuntuforums.org/showthread.php?t=186003)

The problem is that the inspiron somehow overheats, even when it's pretty idle. Mine shuts itself down when the CPU temperature exceeds 75 C. This problem only exists when the power is pluged in. On battery, the idle temperature is around 50 C. One has to give it to Windows that under similar circumstances, my temperature would only be around 30 C. So it's definitely a software issue. 

I was able to fix the worst behavior, that with the power plugged in, under KDE (release 3.5.8 , I actually installed KDE just for that purpose). Under Actions, go to
Settings>Power Control>Laptop Battery

On the right (may require scrolling) there is a panel called
APCI config. You will likely find that nothing is enabled.
Enable CPU throttling (use the "Setup Helper Application" button first if necessary.) Then, on the Power Contol panel,
enable CPU throttle in the "powered" box, and set it to 25% or so. Click OK.

With these measure, I find that the powered behaviour is now essentially the same as when the system runs on
battery, and the idle CPU temperature is around 50 C.
At least it will not power itself of any more.

I haven't figured out yet how to do equivalent steps under gnome. It might also be in the long thread linked above,
but I haven't found it yet (though people asked it many times there). If someone knows, it would be great if that person could post it here.

---

### Post by John Matrix on 2007-12-30
By the way, even after setting the CPU throttle to 25%,  the output of
cat /proc/acpi/processor/CPU0/throttling
is 

state count:             8
active state:            T0
states:
   *T0:                  00%
    T1:                  12%
    T2:                  25%
    T3:                  37%
    T4:                  50%
    T5:                  62%
    T6:                  75%
    T7:                  87%

Hence my CPU is not actually being throttled all the time, but  the temperature remains acceptable.

---

