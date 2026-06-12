---
title: "Reboots + VNC"
date: 2013-01-05
forum: Desktop Environments
---

### Post by GJLenon on 2013-01-05
I built a HDTV box from a Biostar NM70I-847 MB with onboard Intel Graphics. I am experiencing random reboots. I have thrown syslog, dmesg, xorg logs, and everything else I can think of on a tail -f stream and nothing is shown before the reboot. 

At first I was running Mythbuntu and thought that was the problem. I switched to Ubuntu and it still happened, though less when the Myth backend was not running. 

Somehow I figured out that while the machine has an active VNC connection the machine becomes stable. 

I know most people will suggest hardware failure, but I can assure you I have checked/swapped every piece of hardware involved. I have also tried Mythbuntu, Ubuntu 32b, and Ubuntu 64b, with all results the same. The machine is stable under a Win7 install.

Why does the machine reboot continuously when there is no open VNC socket?

---

