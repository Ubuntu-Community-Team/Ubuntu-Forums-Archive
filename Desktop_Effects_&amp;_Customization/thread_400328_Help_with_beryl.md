---
title: "Help with beryl"
date: 2007-04-03
forum: Desktop Effects &amp; Customization
---

### Post by pappy on 2007-04-03
Hi all
I tried to install beryl in Kubuntu 6.10. The installation was ok no problems appeared.After rebooting the machine there was no beryl diamond in system tray but i have 2 new programs under the Setting menu
Beryl setting Manager
Emerald Theme Manager
Both are working but i don't have beryl.
I have the latest nvidia drivers i think
The configuration of the machine
Athlon XP 2800+
1.5GB RAM
GeForce 7600 256MB AGP
Abit Nvidia 2 chipset motherboard
Kubuntu 6.10 with all updates
Thank you for your help

Any ideas?

---

### Post by Waappu on 2007-04-03
Hi

Press Alt+F2 and type ```
beryl-manager
```

---

### Post by pappy on 2007-04-03
I did what you said but the desktop goes black and freezes. Then i have to restart the Xserver (Ctrl+Alt+BackSpace)
Any idea what is wrong?
Cheers

---

### Post by pappy on 2007-04-03
BTW this the output from glxinfo | grep OpenGL

OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GS/AGP/SSE/3DNOW!
OpenGL version string: 2.0.2 NVIDIA 87.76
OpenGL extensions:

---

### Post by pappy on 2007-04-03
Hello i tried to run beryl manager from console
typed beryl-manager and i got this in the console
X Error: BadDevice, invalid or uninitialized input device 169
Major opcode:147
Minor opcode:3
Resource id: 0x0
Failed to open device
XGL Absent, checking for NVIDIA
Nvidia Present
Relaunching beryl with_GL_YIELD= "NOTHING"

and of course the screen goes black and freezes although i could still the music it was playing by the time i did all this!
Any idea what all this mean?
thank you

---

