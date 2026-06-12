---
title: "Ubuntu System Profile?"
date: 2006-01-25
forum: Desktop Environments
---

### Post by chagrins on 2006-01-25
Hi,

Sorry if this has been mentioned before, but I couldn't find it after searching.

I'm looking for a program that will give me a readout of my system specs, similar to the Apple System Profiler on Mac OS X. Processor speed, RAM, etc. I think there's one already installed with Ubuntu, (command line or GUI), but I can't really make head or tail of the info in Device Manager. Any recommendations?

---

### Post by ekarni on 2006-01-25
This may not be entirely what you're looking for, but try:
```

$> cat /proc/cpuinfo
$> cat /proc/meminfo

```

Also try searching for "sensors" if you want a graphical frontend that will give you more info.  I'm using the KSensors frontend to lm-sensors on gnome and it works well.

EDIT:  just saw this very similar thread [http://www.ubuntuforums.org/showthread.php?t=121567]("http://www.ubuntuforums.org/showthread.php?t=121567")
 you can also try the command  lshw  which should be more like what you're looking for

---

### Post by mcduck on 2006-01-25
I don't know about single command, but here are some that may help:

lspci - pretty complete list of all devices
cat /proc/cpuinfo - info about cpu
cat /proc/meminfo - same thing for memory
sensors - if you have lm-sensors installed and configured this will give you temperatures, voltages and fanspeeds.
top -  about running processes and their memory and cpu usage. press q to exit.

---

### Post by chagrins on 2006-01-26
Thanks for your responses! All of those are quite helpful.

---

