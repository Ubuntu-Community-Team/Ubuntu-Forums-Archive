---
title: "Frozen root account (possibly)"
date: 2006-10-03
forum: Desktop Environments
---

### Post by ineluki12 on 2006-10-03
Hello all,
I'm using Xubuntu (Dapper), and I have this strange problem where every now and then, anything that requires root access will stop working, as well as network access. If I try /etc/init.d/networking restart, it will dhcp release and then freeze as it tries to bring the interfaces back up. If I try to restart the system by clicking the quit icon, nothing happens. If I pop up a terminal and sudo reboot, nothing happens. Applications that use gksudo don't work, as I don't even get prompted for a password. To get my system back to normal, I have to kill power and reboot. Any ideas?

Edit: Killing X with ctl-alt-backspace and logging back in does not help. If I kill X and click reboot without logging back in, it seems to shutdown properly, but it ends up at a login prompt (as if I hit ctrl-alt-F1 during normal operation). At this prompt, it doesn't respond to anything, so I'm still forced to kill power.

---

### Post by ciscosurfer on 2006-10-04
First read this ([https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)) to understand what and how to use sudo.

To release your interface and then bring it back up, try issuing```
sudo ifdown eth0
sudo ifup eth0
[COLOR=Blue] OR IF USING ETH1[/COLOR]
sudo ifdown eth1
sudo ifup eth1
```

---

### Post by kerry_s on 2006-10-04
What's your specs? If you have low memory it could seem like the system freezes while moving stuff to swap. You do have swap right?

---

### Post by ineluki12 on 2006-10-04
ciscosurfer,
I should have been more specific. Anything that requires root privilages doesn't seem to work; not the root account itself. I'm quite familiar with sudo.

kerry_s,
Brand new computer; it's definitely not my specs, and my system is pretty much the default setup, as far as partitions and the such are concerned.

I've been checking syslog and it looks like I still have a problem that I thought was solved. My wireless IP is changing about every 2 or 3 minutes. I've also noticed that the whole root-privilage freeze doesn't occur until after I've tried bringing the interface down and back up or tried /etc/init.d/networking restart. I recently downloaded the latest Dell driver, and I downloaded and compiled the newest ndiswrapper, but I think one of these might be the problem.

---

