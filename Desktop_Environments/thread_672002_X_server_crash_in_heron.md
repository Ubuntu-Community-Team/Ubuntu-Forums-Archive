---
title: "X server crash in heron"
date: 2008-01-19
forum: Desktop Environments
---

### Post by robwicks on 2008-01-19
The X server in Heron crashes for me, usually after 20-30 minutes. It's done this several times now. The old X11 log shows:

(--) Mouse0: PnP-detected protocol: "ExplorerPS/2"
(II) Mouse0: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
SetGrabKeysState - disabled

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x7e) [0x80c750e]
1: [0xb7f23420]

Fatal server error:
Caught signal 11.  Server aborting


I am using the nvidia restricted drivers on an AMD Athlon 64X2 4200 on an ECS NFORCE4M-A V3.0 motherboard with 4GB RAM on the 32 bit release. Has anyone else seen this sort of thing? It just started happening after the last xserver-core updates.

---

### Post by HellMind on 2008-01-20
Same here Hady Heron 
Nvidia 169.07

I think it dies when the 3d is being enable

---

### Post by wolf08 on 2008-01-21
I have the same problem, however I am running kwin (kde4) with opengl effects enabled. It seems to crash fairly randomly, although I _think_ each time as been after I opened a new tab in konqueror (both kde3 and kde4). Could there bee some texture problems or memory issues? The crashes seem to always happen while I'm working. For example, I left the computer on overnight and it was still working fine. 

My setup:
X2 3800+
ASUS something or other sli-delux
2xNvidia 7600GTs (One from XFX one generic)
Nvidia 169.07 drivers
Kubuntu Hardy Development

Is anyone using this driver and NOT experiencing these crashes?

---

### Post by jimbo99 on 2008-01-21
They updated the xserver-core files 2 times in 3 days.  You will need to reinstall the nvidia drivers and  you should be back in shape.

---

