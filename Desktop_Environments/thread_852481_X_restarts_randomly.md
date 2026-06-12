---
title: "X restarts randomly"
date: 2008-07-07
forum: Desktop Environments
---

### Post by cactaur on 2008-07-07
I'm currently running Ubuntu Hardy and there are times (about once a day perhaps) that the Xserver would just randomly decide to restart and send me to the login screen. I'm not too sure it's a system load issue because there have been times where the load was much higher and nothing in particular happened. I have an ATI Radeon 9550 and using the open source ATI drivers w/ compiz enabled. That being said, I've looked through the logs, and I found this entry in /var/log/daemon.log: > Jul  7 10:35:15 gregory-desktop gdm[6167]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 

I've also looked for warnings in Xorg.0.log, and haven't found anything too suspicious, just these which don't seem in particular to be connected to the restart: ```
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) RADEON: No matching Device section for instance (BusID PCI:1:0:1) found
(WW) RADEON(0): No crtc mode list for crtc 1,continuing with desired mode
(WW) RADEON(0): DRI init changed memory map, adjusting ...
(WW) RADEON(0):   MC_FB_LOCATION  was: 0xefffe000 is: 0xefffe000
(WW) RADEON(0):   MC_AGP_LOCATION was: 0xffffffc0 is: 0xf07ff000
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(WW) Configured Mouse: No Device specified, looking for one...

```

I don't know what could have possibly caused these restarts. They're not too bad, but can get kinda annoying. If anyone has some advice, it'll be appreciated.

---

### Post by jamesapnic on 2008-07-07
This actually seems to be an open bug, maybe you could try building your own X server from source however, incase its a ubuntu introduced one if you are adept at such things.  Alternatively post your specs on:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/128207](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/128207)

---

