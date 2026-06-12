---
title: "Help: Lucid Lynx is completely unresponsive with 100% CPU usage"
date: 2010-05-29
forum: Desktop Environments
---

### Post by rsanchez1 on 2010-05-29
I did a clean install of Lucid Lynx on an old computer, Pentium 4 @ 2.40 Ghz, 1.5GiB RAM, and the system response is often very sluggish. It takes many seconds to minimize/maximize windows and navigate through menus, where on other installs of Lucid Lynx I have, the system is extremely responsive, nearly instantaneous where it takes the older system seconds. 

I added the System Monitor applet to my panel, and it routinely shows 100% processor usage. But when I open System Monitor with nothing else open, the process that's using the highest %CPU is gnome-system-monitor itself, most of the time hovering under 10% CPU usage, with all other processes showing 0% usage. 

I cannot yet access the internet on that machine, so I have not been able to do updates, but I don't know why the system would be so unresponsive. It's a completely fresh install, and from the start it was sluggish. What can I do to diagnose the problem?

Also, how can I update my system without direct internet access? Is there a way I can just download the updates on a separate machine and transfer them to the one without internet access?

Many thanks for any assistance in solving this issue.

---

### Post by wilee-nilee on 2010-05-29
I would install htop you can do it from the terminal. ```
sudo apt-get install htop
```
Once installed you open a terminal and type htop it will show you what is running and you can kill or turn off whatever is causing this, at the least you can see what is taking all the cpu.

---

### Post by Barafu Albino Cheetah on 2010-05-29
Your swap partition is physically damaged. With bad sectors or some other crap. Try disabling swap. 
Or you have a bad combination of BIOS settings. May be something regarding CPU energy saving. Try disabling floppy drive too, Lynx has stupid problems with floppies.

---

### Post by Chris J on 2010-05-29
I'm having the same problem with a new Lucid install. System Monitor shows 98-100% usage all the time but there is no process listed showing more than about 20% CPU usage. Disabling swap did not help and htop shows no big resource hog. 

There is no floppy drive in this system and the bios settings seem OK according to the information I have at hand. The BIOS is the latest version for this machine as well.

I wouldn't call the system totally unresponsive, but it is pretty slow compared to Karmic, which worked pretty well on this machine..

---

