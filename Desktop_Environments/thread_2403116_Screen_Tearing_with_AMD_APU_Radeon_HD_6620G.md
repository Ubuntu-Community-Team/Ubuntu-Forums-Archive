---
title: "Screen Tearing with AMD APU Radeon HD 6620G"
date: 2018-10-07
forum: Desktop Environments
---

### Post by jetman350 on 2018-10-07
I'm really wanting to install KDE 18.04 on my new project laptop but want to make sure I'll be able to get the Screen Tearing under control. This is not just KDE, it's all Linux Distros I've ever tried. Though I've heard people using other distros with no screen tearing, or made some changes to fix it. The only tearing I experience is when in Browsers, but making any changes in the browsers don't help. I just tried this fix but I assume because I'm in a Live Session it won't work because I cannot reboot. I did log out and back in but that of course did not work. In fact, I don't know if it should be called Screen Tearing, but maybe Chattering while scrolling.
[https://learnubuntumate.weebly.com/screen-tearing-on-amd-graphics.html](https://learnubuntumate.weebly.com/screen-tearing-on-amd-graphics.html)

Here is my info, hopefully it will help to get me going on this new project. I have a nice new HDD and would really like to get this thing going soon!

Thanks in advance!

```
[COLOR=#636363][FONT=Menlo]ubuntu@ubuntu:~$ inxi -Fxz[/FONT][/COLOR]
[COLOR=#636363][FONT=Menlo]System:    Host: ubuntu Kernel: 4.15.0-20-generic x86_64 bits: 64 gcc: 7.3.0[/FONT][/COLOR]
[COLOR=#636363][FONT=Menlo]           Desktop: KDE Plasma 5.12.4 (Qt 5.9.5) Distro: Ubuntu 18.04 LTS[/FONT][/COLOR]
[COLOR=#636363][FONT=Menlo]Machine:   Device: laptop System: Hewlett-Packard product: HP Pavilion dv6 Notebook PC v: 0691210000204610000620100 serial: N/A[/FONT][/COLOR]
[COLOR=#636363][FONT=Menlo]           Mobo: Hewlett-Packard model: 1805 v: 33.58 serial: N/A BIOS: Hewlett-Packard v: F.1C date: 01/25/2013[/FONT][/COLOR]
[COLOR=#636363][FONT=Menlo]Battery    hidpp__0: charge: N/A condition: NA/NA Wh model: Logitech Wireless Mouse M325 status: Discharging[/FONT][/COLOR]
[COLOR=#636363][FONT=Menlo]CPU:       Quad core AMD A8-3520M APU with Radeon HD Graphics (-MCP-) arch: Fusion rev.0 cache: 4096 KB[/FONT][/COLOR]
[COLOR=#636363][FONT=Menlo]           flags: (lm nx sse sse2 sse3 sse4a svm) bmips: 12777[/FONT][/COLOR]
[COLOR=#636363][FONT=Menlo]           clock speeds: max: 1600 MHz 1: 808 MHz 2: 808 MHz 3: 983 MHz 4: 799 MHz[/FONT][/COLOR]
[B][COLOR=#636363][FONT=Menlo]Graphics:  Card: Advanced Micro Devices [AMD/ATI] BeaverCreek [Radeon HD 6620G] bus-ID: 00:01.0[/FONT][/COLOR]
[/B][COLOR=#636363][FONT=Menlo]           Display Server: x11 (X.Org 1.19.6 ) driver: radeon Resolution: 1366x768@59.99hz[/FONT][/COLOR]
[COLOR=#636363][FONT=Menlo]           OpenGL: renderer: AMD SUMO (DRM 2.50.0 / 4.15.0-20-generic, LLVM 6.0.0)[/FONT][/COLOR]
[COLOR=#636363][FONT=Menlo]           version: 3.3 Mesa 18.0.0-rc5 Direct Render: Yes[/FONT][/COLOR]
[COLOR=#636363][FONT=Menlo]Audio:     Card-1 Advanced Micro Devices [AMD] FCH Azalia Controller driver: snd_hda_intel bus-ID: 00:14.2[/FONT][/COLOR]
[COLOR=#636363][FONT=Menlo]           Card-2 Advanced Micro Devices [AMD/ATI] BeaverCreek HDMI Audio [Radeon HD 6500D and 6400G-6600G series][/FONT][/COLOR]
[COLOR=#636363][FONT=Menlo]           driver: snd_hda_intel bus-ID: 00:01.1[/FONT][/COLOR]
[COLOR=#636363][FONT=Menlo]           Sound: Advanced Linux Sound Architecture v: k4.15.0-20-generic[/FONT][/COLOR]
[COLOR=#636363][FONT=Menlo]Network:   Card-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller[/FONT][/COLOR]
[COLOR=#636363][FONT=Menlo]           driver: r8169 v: 2.3LK-NAPI port: 2000 bus-ID: 01:00.0[/FONT][/COLOR]
[COLOR=#636363][FONT=Menlo]           IF: eno1 state: down mac: <filter>[/FONT][/COLOR]
[COLOR=#636363][FONT=Menlo]           Card-2: Broadcom Limited BCM4313 802.11bgn Wireless Network Adapter[/FONT][/COLOR]
[COLOR=#636363][FONT=Menlo]           driver: bcma-pci-bridge bus-ID: 02:00.0[/FONT][/COLOR]
[COLOR=#636363][FONT=Menlo]           IF: wlp2s0b1 state: up mac: <filter>                                                                                                                                                 [/FONT][/COLOR]
[COLOR=#636363][FONT=Menlo]Drives:    HDD Total Size: 144.1GB (26.7% used)                                                                                                                                                 [/FONT][/COLOR]
[COLOR=#636363][FONT=Menlo]           ID-1: /dev/sda model: WDC_WD800BEVS size: 80.0GB temp: 49C                                                                                                                           [/FONT][/COLOR]
[COLOR=#636363][FONT=Menlo]           ID-2: USB /dev/sdb model: USB_Flash_Drive size: 32.0GB temp: 0C    [/FONT][/COLOR]
```

---

