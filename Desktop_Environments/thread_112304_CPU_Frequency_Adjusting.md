---
title: "CPU Frequency Adjusting"
date: 2006-01-04
forum: Desktop Environments
---

### Post by hopspitfire on 2006-01-04
Usually with acpi, when click on the battery you can adjust how fast the processor runs, used to either give you more or less battery life (depending on your circumstances). The problem is, I do not know where it is and how to install it. It was already configured on the other distros I tried, and was wondering how to do this, since my laptop is running at 25% its capacity and it is driving me nuts. Any suggestions? Thanks in advance.

-mc
Owner of [http://www.clanhop.com](http://www.clanhop.com)

---

### Post by 23meg on 2006-01-04
You can use the CPU frequency scaling monitor applet to manually adjust the speed of your processor while powernowd isn't running. To do that, enter ```
sudo chmod +s /usr/bin/cpufreq-selector
``` in a terminal and add the applet to your Gnome panel. To kill powernowd you can use ```
sudo killall powernowd
```

---

### Post by hopspitfire on 2006-01-04
It worked great, thank you! One last question though, will it load like this automatically at next startup or do I need to add something in the modprobe (i'm very new at this)

-mc
Owner of [http://www.clanhop.com](http://www.clanhop.com)

---

