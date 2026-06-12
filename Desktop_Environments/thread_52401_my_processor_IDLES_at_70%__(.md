---
title: "my processor IDLES at 70%  :("
date: 2005-07-27
forum: Desktop Environments
---

### Post by kerinin on 2005-07-27
pIII (i think) 900 mhz processor with 256megs RAM and 30Gig hard drive, running a new install of ubuntu with a few extra progs installed.  when the system first starts up the processor drops to 0% and stays there until i do something, but after a few hours (it may be a specific program like firefox or xine triggering it but i'm not sure) the processor starts to hang at 70% usage when the system is just sitting there, and that's a minimum.  it does it all night and every day, the only way to get it to slow down is to reboot X.

the process that's eating up my processor is X, here's the process:

```
/usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
``` 

As you can imaging, the seriously slows down any programs that actually need to USE the processor.  does anyone have any idea what could be causing this?

---

### Post by JonahRowley on 2005-07-27
What else is running?  X doesn't do anything by itself, something has to be using it.  What other processes are using CPU resources?  Maybe post the output of **top -b -n 1**?

---

