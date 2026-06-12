---
title: "vino crashes, unable to reconnect VNC, with dummy video card"
date: 2022-09-30
forum: Desktop Environments
---

### Post by martin90 on 2022-09-30
My MythTV server/backend (Ubuntu v20.04, default gnome desktop) is in another room without a monitor or keyboard, just power and ethernet. I enabled Media Sharing on the Network card (fixed address setup by the router), and installed the xserver-xorg-video-dummy to solve the blank screen problem. I presume 'vino' is the default VNC server installed and used.

On my main computer (Ubuntu v22.04.1), I use Remmina to initiate a VNC session. Sometimes when I initiate Server Software, the remote session ends. I just did a fresh reboot, remote connected, open Settings, it hesitated too long and session ended. "Unable to connect to VNC server" appears until I reboot again.


I would like to know where to look in the logs for why it's crashing, and how to reset it.


I presume my problem has something to do with a consecutive switch of network cards. Server was originally on a 2008-era "Acer-1" desktop computer with a problem of loose onboard connectors (VGA, NIC, etc.). When network started acting up, I installed a spare PCI NIC I had, enabled network card sharing, didn't like it for some reason, switched to another PCI NIC card, enabled sharing... This summer, I bought a new computer (HP), so I swapped my SSD to the new HP hardware, the old desktop computer (Acer-2) became the new MythTV server when I swapped the HDD from the old "Acer-1", using its onboard NIC. Yet, another network card sharing enabled.

Anyways, VNC worked well before the switcheroo, and would like to fix the crashing problem. (Yes, I can rename xorg.conf (to disable video-dummy), bring the computer here, plug to a monitor and keyboard to perform tasks).

Thanks for any tip.

---

