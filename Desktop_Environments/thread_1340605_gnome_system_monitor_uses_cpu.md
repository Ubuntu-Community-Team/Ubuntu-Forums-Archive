---
title: "gnome system monitor uses cpu?"
date: 2009-11-28
forum: Desktop Environments
---

### Post by expxe on 2009-11-28
i noticed that the cpu usage is around 10%, is that normal, seems high when compared to windows task manager

---

### Post by whoop on 2009-11-28
> **expxe said:**
> i noticed that the cpu usage is around 10%, is that normal, seems high when compared to windows task manager

It is similar on my machine. It uses much cpu because its status is updated frequently, you can lower the speed by increasing the interval in preferences. But it is not a big deal as it only uses cpu when you are using/displaying it.

---

### Post by falconindy on 2009-11-28
Gnome System Monitor operates at the quantum level and roughly follows the Heisenberg Uncertainty Principle.

---

### Post by Vadi on 2009-11-28
Started doing that after they added the fancy graphs in.

---

### Post by expxe on 2009-12-04
im interested in the network bandwidth **counter**, is there a lightweight program for that?

---

### Post by falconindy on 2009-12-04
> **expxe said:**
> im interested in the network bandwidth **counter**, is there a lightweight program for that?
Sure, get the stats off the command line.
```
#!/bin/bash

[[ -z $1 ]] || [[ ! -h /sys/class/net/$1 ]] && echo "Error: Provide a valid network interface" && exit 1

stats=($(cat /proc/net/dev | grep $1 | cut -d: -f2 | awk '{print $1 " " $9}'))

echo Stats for: $1
printf "Received: %5.2fmb\n" $(echo "scale=2;${stats[0]} / 1024 / 1024" | bc -l)
printf "    Sent: %5.2fmb\n" $(echo "scale=2;${stats[1]} / 1024 / 1024" | bc -l)
```
Throw this in a script file (I called it ethstat since netstat is taken).

---

### Post by bluelamp999 on 2009-12-04
Try the *netspeed* panel applet, it's in Synaptic...

---

### Post by akashiraffee on 2009-12-04
> **expxe said:**
> im interested in the network bandwidth **counter**, is there a lightweight program for that?

Check out GKrellM.  It monitors processes, cpu(s), network connections, filesystems, etc etc. and is super configurable.  Like there's plugin's for phases of the moon and earth and probably everything else.  And skins. Tons of crazy skins like some mp3 players have. Looks real nice.  Works real well.

---

### Post by expxe on 2009-12-05
> **bluelamp999 said:**
> Try the *netspeed* panel applet, it's in Synaptic...

i installed it but i can't find it in the menus anywhere after the install.....

---

### Post by bluelamp999 on 2009-12-07
> **expxe said:**
> i installed it but i can't find it in the menus anywhere after the install.....

This is down to a long-standing bug - [https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/21625](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/21625)

To automatically refresh the list inside the "Add" dialog without logging out and logging in again you can restart gnome-panel using the command:

kill -HUP $(pidof gnome-panel)

You should then be able to right click on your panel, select 'Add to panel...' and select the Network Monitor Netspeed applet...

---

