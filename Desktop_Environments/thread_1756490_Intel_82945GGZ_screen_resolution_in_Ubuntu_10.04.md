---
title: "Intel 82945G/GZ screen resolution in Ubuntu 10.04"
date: 2011-05-12
forum: Desktop Environments
---

### Post by paha77 on 2011-05-12
Hello!

I have an Ubuntu 10.04 installation on a Asrock A330GC motherboard with an LCD display connected.  The LCD's native resolution is 1280x1024.

But the system starts in 1024x760 and the native resolution is not in the available modes.

lspci output:

```
...
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
...

```

lshw output:

```

...
        *-display
             description: VGA compatible controller
             product: 82945G/GZ Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:fea80000-feafffff ioport:dc00(size=8) memory:e0000000-efffffff(prefetchable) memory:fea40000-fea7ffff
...

```

How can I configure the system to use it's native resolution?

Thank you.

---

### Post by paha77 on 2011-05-24
Fortunately I've found the solution so here it is for the future queries:

1. Calculate the modeline with **cvt**:

```
root@kiosk-desktop:~# cvt 1280 1024 75
# 1280x1024 74.90 Hz (CVT 1.31M4) hsync: 80.30 kHz; pclk: 138.75 MHz
Modeline "1280x1024_75.00"  138.75  1280 1368 1504 1728  1024 1027 1034 1072 -hsync +vsync

```

Depending on the display the resolution and the refresh rate should be different so be careful with this command.

2. Query current screen parameters with **xrandr**:

```
root@kiosk-desktop:~# xrandr
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 4096 x 4096
**VGA1** connected 1280x1024+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1280x1024_75.00   74.9*+
   1360x768       59.8
   1024x768       60.0
   800x600        60.3     56.2
   848x480        60.0
   640x480        59.9     59.9

```

Please note that the output should be totally different on each screen so this is an example.  The point is the "VGA1" which is the current screen's "alias".

3. Configure the screen with **xrandr**:

```
export DISPLAY=:0
xrandr --newmode **"1280x1024_75.00"  138.75  1280 1368 1504 1728  1024 1027 1034 1072 -hsync +vsync**
xrandr --addmode **VGA1 1280x1024_75.00**
xrandr --output **VGA1 --mode 1280x1024_75.00**

```

You should use the modeline created in step 1 and use VGA1 as seen in step 2.

4. Finalize the setup by changing xorg.conf.  Search the "Monitor" section in Xorg conf (/etc/X11/xorg.conf in Ubuntu) and add these two lines:

```
Section "Monitor"
  Identifier   "Monitor0"
  VendorName   "Monitor Vendor"
  ModelName    "Monitor Model"
  Modeline     **"1280x1024_75.00"  138.75  1280 1368 1504 1728  1024 1027 1034 1072 -hsync +vsync**
  Option       **"PreferredMode" "1280x1024_75.00"**
EndSection

```
5. Restart Xorg (or the machine) to check your results.

Hope this helps.

---

### Post by ChengQikai on 2011-12-20
If you can't find xorg.conf as it is removed from ubunt 10.04 or later.
You can put the command in a sh file, and make it start as the machine starts.
The simplest way is to put it in /etc/rc.local. and insert the command lines above before the last line.

---

