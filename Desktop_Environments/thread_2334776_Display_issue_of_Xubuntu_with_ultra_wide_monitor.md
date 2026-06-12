---
title: "Display issue of Xubuntu with ultra wide monitor"
date: 2016-08-22
forum: Desktop Environments
---

### Post by don.williams on 2016-08-22
Hello folks, 

I have been using Xubuntu 15.04 with xfce on my machine installed with the Nvidia GeForce 315 card, and the display was all good on my old monitor, connected using the VGA cable. Recently I have replaced the old monitor with the new LG ultra wide 34UC98 monitor. When I connect the monitor using the HDMI cable, the resolution is all fine. 

The problem is if I put the mouse cursor in the left edge of the screen or the top left region of the screen, the screen turns blank, and there is no way to get back to the desktop. This happens regardless if I log in (on desktop) or not (on login screen). 

Some of the system information is included below. Do you know if there is a way to fix this?

Thanks!
Don


[FONT=arial]$ xrandr[/FONT]
[FONT=arial]Screen 0: minimum 320 x 200, current 3440 x 1440, maximum 8192 x 8192[/FONT]
[FONT=arial]DVI-I-1 disconnected (normal left inverted right x axis y axis)[/FONT]
[FONT=arial]HDMI-1 connected 3440x1440+0+0 (normal left inverted right x axis y axis) 800mm x 335mm[/FONT]
[FONT=arial]   3440x1440      30.0* [/FONT]
[FONT=arial]   1920x1080      60.0     50.0     59.9  [/FONT]
[FONT=arial]   1680x1050      59.9  [/FONT]
[FONT=arial]   1600x900       60.0  [/FONT]
[FONT=arial]   1280x1024      60.0  [/FONT]
[FONT=arial]   1280x800       59.9  [/FONT]
[FONT=arial]   1152x864       60.0  [/FONT]
[FONT=arial]   1280x720       60.0     50.0     59.9  [/FONT]
[FONT=arial]   1024x768       60.0  [/FONT]
[FONT=arial]   800x600        60.3  [/FONT]
[FONT=arial]   720x576        50.0  [/FONT]
[FONT=arial]   720x480        60.0     59.9  [/FONT]
[FONT=arial]   640x480        60.0     59.9  [/FONT]

[FONT=arial]$ sudo lshw -C video[/FONT]
[FONT=arial]  *-display               [/FONT]
[FONT=arial]       description: VGA compatible controller[/FONT]
[FONT=arial]       product: GT216 [GeForce 315][/FONT]
[FONT=arial]       vendor: NVIDIA Corporation[/FONT]
[FONT=arial]       physical id: 0[/FONT]
[FONT=arial]       bus info: pci@0000:01:00.0[/FONT]
[FONT=arial]       version: a2[/FONT]
[FONT=arial]       width: 64 bits[/FONT]
[FONT=arial]       clock: 33MHz[/FONT]
[FONT=arial]       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom[/FONT]
[FONT=arial]       configuration: driver=nouveau latency=0[/FONT]
[FONT=arial]       resources: irq:31 memory:fa000000-faffffff memory:d0000000-dfffffff memory:ce000000-cfffffff ioport:cc00(size=128) memory:fbd80000-fbdfffff


[/FONT]&#8203;[ATTACH=CONFIG]270807[/ATTACH][ATTACH=CONFIG]270806[/ATTACH]

---

### Post by sudodus on 2016-08-22
It seems you are running outside the specifications of the graphics card. See this link

[geforce-315-oem/specifications](http://www.geforce.com/hardware/desktop-gpus/geforce-315-oem/specifications)

> Display Support
Multi Monitor Yes
Maximum Digital Resolution 2560x1600
Maximum VGA Resolution 2048x1536
Standard Display Connectors VGA HDMI DVI HDMI


So what you get is probably an experimental feature, that is not debugged. I think you should search for a graphics card that can provide the resolution of the monitor, for example nvidia.

You can search the internet for **video card 3440x1440**.

See for example this link: [video-card-3440-1440-resolution-minimum-fps.html](http://www.tomshardware.co.uk/answers/id-3077541/video-card-3440-1440-resolution-minimum-fps.html)

But the next question is: Are there good linux drivers for those cards, GTX 1080, 1070?

Edit: There are simpler cards, that are cheaper, for example GTX 970 that can provide the resolution of your monitor. It is more likely to work with linux, but I don't know. You should browse the internet and try to find out.

---

### Post by Bucky Ball on 2016-08-22
Welcome. And just throwing this in ... 15.04 has reached EOL and hasn't been supported since January. You must be having issues updating it which is a bit of a problem when it comes to security updates if the machine is online. ;)

---

### Post by don.williams on 2016-08-24
Thank you very much for your explanation on the limits of my video card, and on the security issue! :) It seems there are more upgrade work to do.

---

