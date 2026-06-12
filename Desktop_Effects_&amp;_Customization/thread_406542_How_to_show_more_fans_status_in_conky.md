---
title: "How to show more fans status in conky?"
date: 2007-04-11
forum: Desktop Effects &amp; Customization
---

### Post by eentonig on 2007-04-11
I have a conky script that just works very fine, except for one flaw.

I have four fans that are controlled by acpi, and I found that they are indeed switching states one by one if temperature rises. However, the fan that is monitored by the acpifan variable in conky, always shows 'off'

Is there a way to monitor plural fans? Which parameters do I need to include?

---

### Post by tturrisi on 2007-04-11
I use lmsensors to get the fan speeds in Conky.  I use grep & cut to get only the data I want to display.  You can run the commands in a term, changing the cut numbers to determine what numbers you need to use.  You can also run lmsensors in a term to see what names are assigned to your fans.
My server conky.rc
```
$sysname $kernel
Uptime:$alignr$uptime
${time %A}$alignr${time %F}

Hostname:$alignr$nodename
IP:$alignr${addr eth0}

Processes: $processes ${alignr}Running: $running_processes
RAM: $mem/$memmax ${color lightgray}$membar$color
CPU ${cpu cpu1}% ${color lightgray}${cpubar cpu1}$color

hda1 /: ${fs_used_perc /}% ${color lightgray}${fs_bar /}$color
hda6 /home: ${fs_used_perc /home}% ${color lightgray}${fs_bar /home/}$color
Swap: $swapperc% ${color lightgray}$swapbar$color

Fan1: $alignr${execi 300 /usr/bin/sensors | grep fan1 | cut -c11-18}
Fan2: $alignr${execi 300 /usr/bin/sensors | grep fan2 | cut -c11-18}
HD Temp: $alignr${execi 60 hddtemp /dev/hda | cut -c28-29}C
CPU Temp: $alignr${execi 60 /usr/bin/sensors | grep 'CPU Temp' | cut -c15-16}C
MB Temp: $alignr${execi 60 /usr/bin/sensors | grep 'M/B Temp' | cut -c15-16}C

DC/Dulles:
${execi 60 /usr/bin/pymetar KIAD}
```

---

