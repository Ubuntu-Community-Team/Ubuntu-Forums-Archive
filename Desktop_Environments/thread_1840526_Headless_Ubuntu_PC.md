---
title: "Headless Ubuntu PC"
date: 2011-09-07
forum: Desktop Environments
---

### Post by yourgrim666 on 2011-09-07
I'm trying to configure my system to run headless and access the desktop  via VNC when necessary. It seems everytime I unplug the monitor while  ubuntu is running, the system freezes and I am forced to do a hard shut  down. If I start the computer up without a monitor it won't boot up all  the way and I am still unable to access the desktop through VNC. I am  able to VNC to it while there is a monitor attached to it. Automatic  login is enabled. I want to VNC into my ubuntu machine without a  monitor.

---

### Post by Basher101 on 2011-09-07
i guess a normal desktop version will keep giving you bugs...if only VNC is what you want, try setting up a server. Usually servers run without any graphical output, so that issue should not be a problem. You can still install a Desktop Environment to use it like a normal system..

p.s. i can't help you anymore since its midnight here and i gotta get up early for school...good luck

---

### Post by yourgrim666 on 2011-09-07
I appreciate your reply but after signing up and searching around the forum for a few hours, I found a solution that worked for me. I am now able to run my Ubuntu 11.04 machine without a monitor/keyboard/mouse. I simply ran this command in the terminal:

sudo dpkg-reconfigure xserver-xorg

And rebooted. I can now VNC into that machine. Thanks.

---

### Post by MG2R on 2011-09-07
Glad you found a sloution! :)

Please remember to mark the post SOLVED using the 'thread tools' at the top of the page. Thanks!

---

