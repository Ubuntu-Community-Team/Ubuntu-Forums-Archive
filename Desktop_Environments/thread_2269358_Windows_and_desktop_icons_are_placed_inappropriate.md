---
title: "Windows and desktop icons are placed inappropriate to the display resolution"
date: 2015-03-15
forum: Desktop Environments
---

### Post by micha2358 on 2015-03-15
My Ubuntu 14.10 environment seems to use a larger internal resolution than my native display resolution for placing new windowed applications. The resolution in system menu is correct, and the left and top menu bars of Ubuntu are diplayed correct, too. But the dektop icons are too far to the left or top of the desktop, so they are partly hidden under the top dekstop bar and the transparent left menu bar.
Also, when opening a new window-application, it opens either bigger than my desktop's size or a smaller window opens, but half of the window is over the edge of the windows. So i alway need to move/resize the windows to access the scroll bars of the file- or internet browser. So mybe there is a problem with the grid, or pattern for placing these element, which maybe is using a bigger resolution than selected in system menu.

These problems may be annoying, but i could live with them. But there is a bigger impact to that problem: in some games, the screen also juts out of the window and the mouse courser in the game menu is not accurate. To hit the menu items, I have to point the cursor a bit higher upper the menu item.

Any idea how to solve this issue? Maybe there is a config file where i can correct/adapt the pattern to the given display's resolution?

---

### Post by CantankRus on 2015-03-17
You're more likely to get help if you provide some computer details.
You can install inxi to do this via terminal...
```
sudo apt-get install inxi
```

Then copy and paste the output from the terminal command...
```
inxi -b
```

eg
```
**[COLOR="#008000"]glen@Trusty:~$[/COLOR] inxi -b**
**System:**    Host: Trusty Kernel: 3.16.0-31-generic x86_64 (64 bit) Desktop: Gnome Distro: Ubuntu 14.04 trusty
**Machine**:   Mobo: Gigabyte model: GA-78LMT-USB3 version: x.x Bios: Award version: FA date: 04/23/2013
**CPU**:       Quad core AMD FX-4300 (-MCP-) clocked at 1400.00 MHz 
**Graphics**:  Card: NVIDIA GF116 [GeForce GTX 550 Ti] 
           X.Org: 1.16.0 drivers: nvidia (unloaded: fbdev,vesa,nouveau) Resolution: 1680x1050@59.9hz 
           GLX Renderer: GeForce GTX 550 Ti/PCIe/SSE2 GLX Version: 4.4.0 NVIDIA 331.113
**Network**:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller driver: r8169 
**Drives**:    HDD Total Size: 1250.3GB (12.8% used)
**Info**:      Processes: 241 Uptime: 56 min Memory: 1718.7/3934.9MB Client: Shell (bash) inxi: 1.9.17
```

---

### Post by micha2358 on 2015-07-05
Still no fix for the issue :(
Here's the stuff I got from inxi:

```

System:    Host: michael-P5E3-Premium Kernel: 3.19.0-21-generic x86_64 (64 bit)
           Desktop: Unity 7.3.2  Distro: Ubuntu 15.04 vivid
Machine:   Mobo: ASUSTeK model: P5E3 Premium v: Rev 2.xx
           Bios: American Megatrends v: 0803 date: 05/21/2009
CPU:       Quad core Intel Core2 Extreme X9770 (-MCP-)
           speed/max: 2400/3200 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Cypress XT [Radeon HD 5870]
           Display Server: X.Org 1.17.1 drivers: ati,fglrx (unloaded: radeon)
           Resolution: 1680x1050@59.9hz
           GLX Renderer: AMD Radeon HD 5800 Series
           GLX Version: 4.4.12874 - CPC 15.20.1013
Network:   Card-1: Marvell 88E8056 PCI-E Gigabit Ethernet Controller
           driver: sky2
           Card-2: Microsoft Xbox 360 Wireless Adapter
Drives:    HDD Total Size: 4460.9GB (7.6% used)
Info:      Processes: 234 Uptime: 7 min Memory: 1741.9/7983.8MB
           Client: Shell (bash) inxi: 2.2.16

```
I found a workaround: In the system settings, I have to change to a different (not native) resolution, then discard it with esc and voilà, the dektop and it's windows fit perfectly in the screen. But I have to do this every time I boot my system!


So, any idea how to fix it?

---

