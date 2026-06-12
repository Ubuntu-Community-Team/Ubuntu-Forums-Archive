---
title: "Help with radeon video driver"
date: 2016-10-17
forum: Gaming &amp; Leisure
---

### Post by Kevin_Casey on 2016-10-17
Hello,

I'm having trouble loading some steam games that require OpenGl >= 3.3.  I've checked my graphics card on Phronics and it should be supported but I'm only for some reason I'm only seeing OpenGl 3.0.  I've also loaded the obaif ppa but that didn't improve anything.  My graphics card is an R9 270x.  Anyone have any ideas?

```
casey2542@xubuntu:~$ glxinfo | grep version
server glx version string: 1.4
client glx version string: 1.4
GLX version: 1.4
    Max core profile version: 4.2
**    Max compat profile version: 3.0**
    Max GLES1 profile version: 1.1
    Max GLES[23] profile version: 3.0
OpenGL core profile version string: 4.2 (Core Profile) Mesa 12.1.0-devel
OpenGL core profile shading language version string: 4.20
OpenGL version string: 3.0 Mesa 12.1.0-devel
OpenGL shading language version string: 1.30
OpenGL ES profile version string: OpenGL ES 3.0 Mesa 12.1.0-devel
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.00
casey2542@xubuntu:~$ sudo lshw -c video
  *-display               
       description: VGA compatible controller
       product: Curacao XT [Radeon R7 370 / R9 270X/370 OEM]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:29 memory:c0000000-cfffffff memory:dfe00000-dfe3ffff ioport:e000(size=256) memory:dfe40000-dfe5ffff
casey2542@xubuntu:~$ uname -r
4.4.0-43-generic




```

Thanks!

---

### Post by howefield on 2016-10-17
Thread moved to the "*Gaming & Leisure*" forum for a better fit.

---

### Post by oldrocker99 on 2016-10-17
The radeon driver **should** support OpenGL 3.3 and 4.0. Try uninstalling and reinstalling the radeon driver. Post your results here.

---

### Post by Kris_M on 2016-10-21
Welcome to the forum!
Did you actually install a driver or you using what came with Ubuntu?
Might look at this:
[https://ubuntuforums.org/showthread.php?t=2340326](https://ubuntuforums.org/showthread.php?t=2340326)

---

### Post by briankorthals-l on 2016-10-27
I am also having issues with this while using an A10-7300 Kaveri integrated graphics chip

---

### Post by Kevin_Casey on 2016-10-31
Replaced with a GTX 1060.  Problem solved.  Finally earned my lesson trying to get AMD hardware to work.  Had to replace the processor (FX 8350) about 6 months ago due to random lockups.  Never again.  Spend the extra money - well worth it.

---

### Post by Kevin_Casey on 2016-10-31
```

                          ./+o+-       casey2542@xubuntu
                  yyyyy- -yyyyyy+      OS: Ubuntu 16.04 xenial
               ://+//////-yyyyyyo      Kernel: x86_64 Linux 4.7.2-040702-generic
           .++ .:/++++++/-.+sss/`      Uptime: 1d 10h 3m
         .:++o:  /++++++++/:--:/-      Packages: 2386
        o:+o+:++.`..```.-/oo+++++/     Shell: bash 4.3.46
       .:+o:+o/.          `+sssoo+/    Resolution: 3840x1080
  .++/+:+oo+o:`             /sssooo.   DE: XFCE
 /+++//+:`oo+o               /::--:.   WM: Xfwm4
 \+/+o+++`o++o               ++////.   WM Theme: Greybird
  .++.o+++oo+:`             /dddhhh.   GTK Theme: Greybird [GTK2]
       .+.o+oo:.          `oddhhhh+    Icon Theme: Vibrancy-Dark-Blue-Vivid
        \+.++o+o``-````.:ohdhhhhh+     Font: Ubuntu 10
         `:o+++ `ohhhhhhhhyo++os:      CPU: Intel Core i7-4790K CPU @ 8x 4.4GHz
           .o:`.syhhhhhhh/.oo++o`      GPU: GeForce GTX 1060 3GB
               /osyyyyyyo++ooo+++/     RAM: 4918MiB / 15993MiB
                   ````` +oo+++o\:    
                          `oo++. 

```

---

### Post by mastablasta on 2016-11-02
a cheaper option would be to use 14.04 and install catalyst, then use that until opensource drivers catch up.

you used a simpler more expencive solution. as long as it works for you...

---

