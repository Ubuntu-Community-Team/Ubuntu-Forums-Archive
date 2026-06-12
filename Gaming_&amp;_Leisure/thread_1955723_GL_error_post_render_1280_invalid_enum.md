---
title: "GL error: post render 1280: invalid enum"
date: 2012-04-10
forum: Gaming &amp; Leisure
---

### Post by saskiiaa on 2012-04-10
Hi there, I am having a problem and I hope I can get some input! When I  start up minecraft it seems to work just fine until I load my world, at  which point I get the following error over and over again:
########## GL ERROR ########## @ Post render 1280: Invalid enum

On top of that, the blocks don't generate like they should (everything  looks exactly the same) and the screen flickers like crazy.

Here is some info:

```
$ glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
18983 frames in 5.0 seconds = 3793.135 FPS
19648 frames in 5.0 seconds = 3928.286 FPS
19700 frames in 5.0 seconds = 3937.182 FPS

$ lspci -vmk | grep -A 8 -B 2 VGA

Device:    08:00.0
Class:    VGA compatible controller
Vendor:    ATI Technologies Inc
Device:    M92 [Mobility Radeon HD 4500/5100 Series]
SVendor:    Toshiba America Info Systems
SDevice:    Device ffc0
Driver:    fglrx_pci
Module:    radeon

Device:    08:00.1

$ uname -a
Linux saskia-ubuntu 3.0.0-17-generic #30-Ubuntu SMP Thu Mar 8 17:34:21 UTC 2012 i686 i686 i386 GNU/Linux

$ java -version
java version "1.6.0_31"
Java(TM) SE Runtime Environment (build 1.6.0_31-b04)
Java HotSpot(TM) Server VM (build 20.6-b01, mixed mode)
```I do not have the driver installed for my ATI graphics card because that  was giving me another error. That error went away as soon as I  uninstalled the driver.

Well, I've tried a whole bunch of stuff and now I'm really at my wits end. I hope someone can help me out or give me suggestions on what to try next. Thanks in advance!

---

