---
title: "Xubuntu dual monitor, change vertical alignment of horizontally aligned monitors?"
date: 2016-02-02
forum: Desktop Environments
---

### Post by Kilarin on 2016-02-02
I am running Xubuntu 14.04 (32bit) on a laptop with a secondary (higher resolution) monitor attached.  Xubuntu's built in dual monitor functionality is working for me, with one minor annoyance.
My desk is set up so that the external monitor is in front of me, and the laptop is to the right, and DOWN.   So they are aligned so that the top of the laptop monitor lines up with about the middle of the desktop monitor.  And the bottom of the laptop monitor is below the bottom of the desktop monitor.

With this setup, it is intuitive to drag the mouse from the external monitor to the right and DOWN to get to the laptop, but that won't work because Xubuntu defaults to having the tops of the monitors aligned.  Since the resolutions are different, this means that there is a "dead" area at the bottom right corner of the desktop monitor that the cursor won't go past.  You have to move it up to get it to go over to the other monitor.  

This isn't a big deal, it's just a small annoyance, but does anyone know how to change the vertical alignment of horizontally aligned dual displays in Xubuntu?  Can it be done through xrandr and the command line?

thanks,

---

### Post by Kilarin on 2016-02-09
well, I solved the problem PARTIALLY

sudo apt-get install arandr
arandr

gives a nice gui that lets me change how the monitors line up vertically as well as just left and right.
to produce my desired alignment
```

/----------------------\
|                      |
|                      | /---------------\
|                      | |               |
|                      | |               |
|                      | |               |
\----------------------/ \---------------/

```
instead of the default with the tops aligned.

You can save to a script like this:
#!/bin/sh
xrandr --output LVDS --mode 1366x768 --pos 1920x312 --rotate normal --output CRT1 --off --output DFP4 --off --output DFP5 --off --output DFP2 --off --output DFP3 --off --output DFP1 --mode 1920x1080 --pos 0x0 --rotate normal

NOW, I just have to figure out how to make this permanent so I don't have to run the script every time.

I tried adding it to sessions and startup:

Whisker menu button > All Settings -> under System click "Session and Startup"
Application Autostart tab -> Add Button
Name=Dual-monitors XFCE
Desc=Dual monitors XFCE
Command=xrandr --output LVDS --mode 1366x768 --pos 1920x312 --rotate normal --output CRT1 --off --output DFP4 --off --output DFP5 --off --output DFP2 --off --output DFP3 --off --output DFP1 --mode 1920x1080 --pos 0x0 --rotate normal

But it doesn't seem to be working, something must be automatically realigning the monitors the way xubuntu wants them to be (with the tops lined up).

anyone know how I can set the --pos option to be permanent in a config file?  Do I have to create an /etc/X11/xorg.conf ??  I'm a little nervous about doing that because it doesn't exist by default and I understand that if you set it up wrong you will not be able to boot to the gui.

Any advice still much appreciated.

---

