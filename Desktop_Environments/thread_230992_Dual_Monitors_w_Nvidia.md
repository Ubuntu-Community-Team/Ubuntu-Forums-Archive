---
title: "Dual Monitors w/ Nvidia"
date: 2006-08-06
forum: Desktop Environments
---

### Post by cbrack on 2006-08-06
Hello all,  I'm new to the community, and for the most part, to Ubuntu.  I'm pretty familiar with linux, however.

I've been using windows for quite some time now, and I set up kubuntu on my pc, and I would like to get my second monitor working as an extended desktop.  I've been looking non-stop for a solution, to no avail.  

I followed a guide to download the newest nvidia drivers for my 6800GS, and in the process it edited my Xorg.conf file.  That seems to be the cause of my problem:  when the xorg.conf file is edited under the "Device" section, and I restart x, the Kubuntu logo will pop up with an empty process bar and will hang.  

I can hit ctrl+alt+f1 and get terminals and do whatever i want, but i still can't do anything without booting a live CD and replacing the edited xorg.conf with my backup.  

If anyone knows of a good reliable dual-monitor guide, or can help me out with this current problem, I would very much appreciate it.


Thanks,

Chris

[Edit] Also, its PCI-Express... Don't know if that makes a difference.

---

### Post by cbrack on 2006-08-06
Well, we figured everything out... Turns out when we installed the nvidia drivers through apt get for the first time, it didn't work properly... With enough toying we got the driver to install, and everything works now.  Hopefully this might help anyone with the same problem.

Thanks

---

