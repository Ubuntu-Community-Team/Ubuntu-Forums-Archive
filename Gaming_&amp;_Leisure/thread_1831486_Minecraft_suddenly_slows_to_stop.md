---
title: "Minecraft suddenly slows to stop"
date: 2011-08-23
forum: Gaming &amp; Leisure
---

### Post by tomkat3 on 2011-08-23
Well, here's what keeps happening: I'll play Minecraft (fast graphics, normal render distance) just fine for about 30 minutes with no problems. At random (often when I explore new areas, I think) the game suddenly becomes really slow. If I'm walking around, I'll be frozen in one place for a minute, then jump 60 blocks ahead. Jerky slow. I look down to the little xfce CPU graph and it'll be using 100% of my CPU (instead of the usual 40-50%.

I'm using Xubuntu 11.04 on a Dell d630 laptop with the nvidia card below. I tried playing minecraft in windows 7, but it consistently caused the graphics driver to crash. For some reason, when I played on Ubuntu (I recently upgraded from Ubuntu 10.04) it worked great.

If this helps:
```

sudo lshw -class display
  *-display              
       description: VGA compatible controller
       product: G86M [Quadro NVS 135M]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:f5000000-f5ffffff memory:e0000000-efffffff memory:f2000000-f3ffffff ioport:df00(size=128) memory:f4000000-f401ffff

```

Here's what it looks like when I run it from the terminal. Some of the initial errors look pretty scary, but like I said, it works fine at first. I don't think it printed any new error messages when the slowdown started.

```

$ java -jar minecraft.jar 
java.io.IOException: Cannot run program "javaw": java.io.IOException: error=2, No such file or directory
    at java.lang.ProcessBuilder.start(ProcessBuilder.java:475)
    at net.minecraft.MinecraftLauncher.main(MinecraftLauncher.java:31)
Caused by: java.io.IOException: java.io.IOException: error=2, No such file or directory
    at java.lang.UNIXProcess.<init>(UNIXProcess.java:164)
    at java.lang.ProcessImpl.start(ProcessImpl.java:81)
    at java.lang.ProcessBuilder.start(ProcessBuilder.java:468)
    ... 1 more
16 achievements
151 recipes
Setting user: tomkat5, -3798173204163560242
Loading: net.java.games.input.LinuxEnvironmentPlugin
Failed to open device (/dev/input/event10): Failed to open device /dev/input/event10 (13)

Failed to open device (/dev/input/event9): Failed to open device /dev/input/event9 (13)

Failed to open device (/dev/input/event8): Failed to open device /dev/input/event8 (13)

Failed to open device (/dev/input/event7): Failed to open device /dev/input/event7 (13)

Failed to open device (/dev/input/event6): Failed to open device /dev/input/event6 (13)

Failed to open device (/dev/input/event5): Failed to open device /dev/input/event5 (13)

Failed to open device (/dev/input/event4): Failed to open device /dev/input/event4 (13)

Failed to open device (/dev/input/event3): Failed to open device /dev/input/event3 (13)

Failed to open device (/dev/input/event2): Failed to open device /dev/input/event2 (13)

Failed to open device (/dev/input/event1): Failed to open device /dev/input/event1 (13)

Failed to open device (/dev/input/event0): Failed to open device /dev/input/event0 (13)

Linux plugin claims to have found 0 controllers

Starting up SoundSystem...
Initializing LWJGL OpenAL
    (The LWJGL binding of OpenAL.  For more information, see http://www.lwjgl.org)
OpenAL initialized.

Stopping!

SoundSystem shutting down...
AL lib: alBuffer.c:1081: exit(): deleting 6 Buffer(s)
    Author: Paul Lamb, www.paulscode.com


```

---

