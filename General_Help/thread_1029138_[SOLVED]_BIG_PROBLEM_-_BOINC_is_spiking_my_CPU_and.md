---
title: "[SOLVED] BIG PROBLEM - BOINC is spiking my CPU and crashing my computer after I unins"
date: 2009-01-03
forum: General Help
---

### Post by hotweiss on 2009-01-03
I downloaded BOINC from getdeb.net and installed it, but a minute into using it my computer crashed and restarted. After the reboot I uninstalled BOINC, but I still noticed that my CPU was spiking because my CPU fan was getting really loud. I looked at the system monitor and my CPU useage was 100%, yet all of the processes were at 0%. Then I installed and ran Htop, and in fact the culprit was BOINC. These 100% spikes are causing my system to crash. To add to the complexity of the problem, the BOINC process comes and goes. It even comes back after I kill it using Htop. Now the problem is: how do I uninstall something that has already been uninstalled?

---

### Post by Sin@Sin-Sacrifice on 2009-01-03
If you can get to a terminal type ```
find boinc
``` or ```
locate boinc
``` or ```
whereis boinc
``` If any of those come up with anything go to and delete all the files.

---

### Post by hotweiss on 2009-01-03
> **Sin@Sin-Sacrifice said:**
> If you can get to a terminal type ```
find boinc
``` or ```
locate boinc
``` or ```
whereis boinc
``` If any of those come up with anything go to and delete all the files.

Thanks I didn't know about the locate command, now I've deleted all of the boinc files. Prior to reading your answer I found a script file in /etc/init.d that was starting it at boot. Thanks for the help.

---

