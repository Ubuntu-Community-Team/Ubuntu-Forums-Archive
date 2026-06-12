---
title: "Unreachable bottom of screen with docky"
date: 2018-09-02
forum: Desktop Environments
---

### Post by gandroz on 2018-09-02
Hi,
I'm using Ubuntu 18.04 with gnome, and docky. Whenever I launch Nautilus, I cannot reach the bottom of the window. For example, say I open a nautilus window to browse my files, I cannot select a file which is at the bottom of the window except if I resize it and move it higher in the screen. I dont have this kind of issue with Chrome for example where all the viewport is reachable, however, I have the issue with a terminal, pycharm etc. It is very annoying and it suddenly appears. The solution is to kill docky process, but that's not what I want as I find docky very usefull.
Any idea on how to fix that ?
Thanks

---

### Post by again? on 2018-09-02
It's usually a graphics/compositing issue where the invisible window of docky isn't composited.
Can be caused if your window manager is reloading.
I am using xfce and I see this when I switch window managers on the fly.
I need to kill and restart plank.
[ATTACH=CONFIG]280955[/ATTACH]

Handy to have relevant specs.
Install inxi (system information script).
If you don't want the recommended dependencies of hddtemp and lm-sensors...
```
sudo apt install [COLOR="#696969"]--no-install-recommends[/COLOR] inxi
```

With recommends
```
sudo apt install inxi
```

Then post the output of
```
inxi -b
```

PS: If you just require a simple dock/launcher try **plank** and see how that fares.

---

### Post by gandroz on 2018-09-04
My issue occured after my motherboard burned and got replaced.... I did not experienced the issue before that.
Here are my informations

```

System:    Host: GuiAnd-P50 Kernel: 4.15.0-33-generic x86_64 bits: 64 Desktop: Gnome 3.28.3
           Distro: Ubuntu 18.04.1 LTS
Machine:   Device: laptop System: LENOVO product: 20EN0013CA v: ThinkPad P50 serial: N/A
           Mobo: LENOVO model: 20EN0013CA v: 0B98417 WIN serial: N/A
           UEFI: LENOVO v: N1EET78W (1.51 ) date: 05/18/2018
Battery    BAT0: charge: 85.9 Wh 100.0% condition: 85.9/90.0 Wh (95%)
CPU:       Quad core Intel Core i7-6700HQ (-MT-MCP-) speed/max: 1122/3500 MHz
Graphics:  Card-1: Intel HD Graphics 530
           Card-2: NVIDIA GM107GLM [Quadro M1000M]
           Display Server: wayland (X.Org 1.19.6 ) drivers: modesetting,nvidia (unloaded: fbdev,vesa,nouveau)
           Resolution: 2560x1440@59.91hz, 1920x1080@59.96hz
           OpenGL: renderer: Mesa DRI Intel HD Graphics 530 (Skylake GT2) version: 4.5 Mesa 18.0.5
Network:   Card-1: Intel Ethernet Connection (2) I219-V driver: e1000e
           Card-2: Intel Wireless 8260 driver: iwlwifi
Drives:    HDD Total Size: 756.2GB (51.8% used)
Info:      Processes: 349 Uptime: 20 min Memory: 4213.1/64249.3MB Client: Shell (bash) inxi: 2.3.56

```

---

### Post by again? on 2018-09-05
I use an old desktop nvidia card which just works and not very clued with laptop graphics
but hopefully this bump will bring it to the attention of those more familiar with your graphics hardware. 

P.S easier to read if you put output between code boxes.
eg
[noparse]```
 paste in inxi output 
```[/noparse]

Will show as...
```
glen@Gubu:~$ inxi -b
System:    Host: Gubu Kernel: 4.15.0-32-generic x86_64 bits: 64
           Desktop: Gnome 3.28.2 Distro: Ubuntu 18.04.1 LTS
Machine:   Device: desktop Mobo: Gigabyte model: GA-78LMT-USB3 v: x.x serial: N/A
           BIOS: Award v: FA date: 04/23/2013
CPU:       Quad core AMD FX-4300 (-MCP-) speed/max: 1405/3800 MHz
Graphics:  Card: NVIDIA GF116 [GeForce GTX 550 Ti]
           Display Server: wayland (X.Org 1.19.6 )
           drivers: nouveau (unloaded: modesetting,fbdev,vesa)
           Resolution: 1680x1050@59.85hz
           OpenGL: renderer: NVCF version: 4.3 Mesa 18.0.5
Network:   Card: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller
           driver: r8169
Drives:    HDD Total Size: 870.2GB (11.1% used)
Info:      Processes: 258 Uptime: 1 min Memory: 1017.6/3926.7MB
           Client: Shell (bash) inxi: 2.3.56
```

---

