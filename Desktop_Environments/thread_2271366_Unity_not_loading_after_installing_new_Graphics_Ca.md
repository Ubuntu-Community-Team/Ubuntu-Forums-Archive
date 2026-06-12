---
title: "Unity not loading after installing new Graphics Card"
date: 2015-03-29
forum: Desktop Environments
---

### Post by MrOstrichman on 2015-03-29
I recently installed an NVidia GeForce 6200 on my ancient computer. After I installed it, I booted Ubuntu 14.10, and everything was working perfectly. I went to the terminal to install the settings program for the card. While doing so, everything became unresponsive. Using Google, I restarted LightDM (from the CTRL-ALT-F1 terminal program), but that didn't work, so I restarted the machine. I tried to load up Unity, but that still didn't work. I rebooted it again, but this time I loaded up Cairo-Dock and uninstalled the settings program. I logged out and into the Guest account, which loaded Unity without any problems. I've uninstalled and reinstalled Unity several times, and I've run out of ideas. Does anyone have an idea?

---

### Post by grahammechanical on 2015-03-29
Was the original graphics adapter also Nvidia? Were you using the Nvidia proprietary video driver? In my opinion, before changing video adapters we should revert to using the open source video driver, which for Nvidia cards is called Nouveau. Otherwise, we might end up with a mis-match between installed video drivers and installed graphic adapters.

When we install a proprietary video driver we also get an appropriate driver setting utility. With Nvidia it is called Nvidia Xserver settings. So, I do not understand why you thought you needed to install the settings program. What command did you run?

You can try this - At the grub boot menu select Advance Options for Ubuntu and in the sub-menu select recovery mode. At the recovery menu select Resume. That should load to the desktop using an open source video driver called llvmpipe. Then go to System Settings>Software and Updates>Additional Drivers tab and try a different video driver. Start with Nouveau.

Also if we a getting to are desktop without the launcher and top panel, then try right clicking the desktop. A menu should appear. Select Change Desktop Background. That will load System Settings at the Appearance utility but from there we can get to Additional Drivers.

There is also something else to consider. The new video adapter might be new to that machine but is it new according to Nvidia? Ubuntu 14.10 has later Nvidia drivers. Which may or may not support that video adapter.  I do not know but it is something to keep in mind. If it is the case you might need to find an older video driver in Software Centre or use the open source video driver.

Regards.

---

### Post by CantankRus on 2015-03-30
So where are you at now?
**grahammechanical** has some good advice and here are some other options.
What happens when you log into your account?
When you mention cairo-dock does that mean you can boot into a  cairo-dock session.
These commands will put a terminal launcher on your desktop which you can use in your normal account ...
```
cp /usr/share/applications/gnome-terminal.desktop ~/Desktop
chmod +x ~/Desktop/gnome-terminal.desktop
```

You can then install inxi to show you what vid drivers are installed and being used...
```
sudo apt-get install inxi
```

Then run ...
```
inxi -b
```
eg
```
**[COLOR="#008000"]glen@Trusty:~$[/COLOR] inxi -b**
System:    Host: Trusty Kernel: 3.16.0-33-generic x86_64 (64 bit) Desktop: Gnome Distro: Ubuntu 14.04 trusty
Machine:   Mobo: Gigabyte model: GA-78LMT-USB3 version: x.x Bios: Award version: FA date: 04/23/2013
CPU:       Quad core AMD FX-4300 (-MCP-) clocked at 1400.00 MHz 
Graphics:  Card: NVIDIA GF116 [GeForce GTX 550 Ti] 
           X.Org: 1.16.0 [COLOR="#FF0000"]**drivers: nvidia (unloaded: fbdev,vesa,nouveau)**[/COLOR] Resolution: 1680x1050@59.9hz 
           GLX Renderer: GeForce GTX 550 Ti/PCIe/SSE2 GLX Version: 4.4.0 [COLOR="#FF0000"]**NVIDIA 331.113**[/COLOR]
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller driver: r8169 
Drives:    HDD Total Size: 1250.3GB (13.3% used)
Info:      Processes: 240 Uptime: 41 min Memory: 1589.4/3934.9MB Client: Shell (bash) inxi: 1.9.17
```
Knowing what drivers are installed and being loaded will be helpful.
For your card I believe you need the legacy 304 driver.

You may need to purge nvidia and reinstall or you just may need to reset and reload unity.

---

