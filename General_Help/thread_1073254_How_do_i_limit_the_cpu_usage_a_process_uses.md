---
title: "How do i limit the cpu usage a process uses"
date: 2009-02-18
forum: General Help
---

### Post by lavinog on 2009-02-18
Is there a way to throttle the cpu cycles a process uses?
For example:
I have a script that will manipulate and convert a bunch of images. I would like to run this in the background on my laptop. Normally it will max out my cpu usage for a while, and my laptop gets really hot. Instead of running the fan at max speed and burning my lap, I would like to just extend the length of time the process takes while reducing the load on the cpu.

I can achieve a similar behavior with scripts that loop by using sleep statements between steps to give the cpu time to dissipate heat. This doesn't work with single commands (such as compressing large archives)

nice helps, but I am looking for even more control.

---

### Post by sdennie on 2009-02-18
One thing you could do would be to force your CPU to the lowest frequency. That would make the whole machine much slower but, it would probably keep the laptop cooler under that kind of load.  To try this use:

```

sudo cpufreq-selector -g powersave

```

Edit:

Another possibility would be to send the process a SIGSTOP signal, sleep for a bit, then send it a SIGCONT signal.  Essentially what you describe above but, using signals to modify the single process.

---

### Post by bettlebrox on 2009-02-18
Install cpulimit, and look at the man page:

```
-l, --limit=N
              percentage of CPU allowed from 0 to 100 (mandatory)

```
:)

---

### Post by Slim Odds on 2009-02-18
[http://ubuntuforums.org/showthread.php?t=992706](http://ubuntuforums.org/showthread.php?t=992706)

---

