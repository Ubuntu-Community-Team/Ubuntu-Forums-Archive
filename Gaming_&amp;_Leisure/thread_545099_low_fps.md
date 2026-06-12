---
title: "low fps"
date: 2007-09-07
forum: Gaming &amp; Leisure
---

### Post by nzadLithium on 2007-09-07
I have a computer its a celeron 2.56 ghz, it has an ati x1300 gfx card. 

I'm trying to play return to castle wolfenstein with these requirements:

    * 3-D Hardware Accelerator (with 16MB VRAM with full OpenGL® support
    * Pentium® II 400 Mhz processor or Athlon® processor
    * English version of Windows® 95 OSR2/98/ME/NT4.0 (SP6)/2000/XP Operating System
    * 128 MB RAM
    * 16-bit high color video mode
    * 800 MB of uncompressed hard disk space for game files (Minimum Install), plus 300 MB for the Windows swap file
    * A 100% Windows® 95 OSR2/98/ME/NT4.0 (SP6)/2000/XP compatible computer system (including compatible 32-bit drivers for CD-ROM drive, video card, sound card and input devices)
    * Quad-speed CD-ROM drive (600 K/sec. sustained transfer rate)
    * 100% DirectX® 8.0a (included)
    * 100% DirectX 3.0 or higher compatible sound card and drivers
    * 100% Microsoft-compatible mouse/keyboard and driver

I am using the linux binary's. 

I would think the specs for that would be similar say:
500mhz processor
linux 
128 mb ram
16-bit high colour video mode

etc.

so theoritically since my computer far surpases these requirements i should be able to get a bit more than the 25 fps (maximum) i am getting.

my settings are all set to minimum.

is there something i need to (or can) do to boost my fps?

---

### Post by ajgreeny on 2007-09-07
What graphics driver is the ati card using, the open source ati that I imagine the system used by default, or have you tried to install the proprietary fglrx driver?

It sounds as if you have a graphic card problem of some sort.  Try glxgears in a terminal and see what fps that reports.  My lower spec system than yours with an amd sempron 2400+ cpu, an ati 9200SE card and 1GB ram gives 880fps using the OS ati driver, and seems to do everything I want it to, though I'm not a gamer.

---

### Post by nzadLithium on 2007-09-07
cmaster@cmaster32bit-desktop:~$ glxgears
1327 frames in 5.0 seconds = 265.202 FPS
1330 frames in 5.0 seconds = 265.789 FPS
1010 frames in 5.0 seconds = 201.839 FPS
699 frames in 5.0 seconds = 139.688 FPS
708 frames in 5.0 seconds = 141.488 FPS
949 frames in 5.0 seconds = 189.650 FPS
1272 frames in 5.0 seconds = 254.198 FPS
1313 frames in 5.0 seconds = 262.391 FPS
1319 frames in 5.0 seconds = 263.590 FPS
1308 frames in 5.0 seconds = 261.392 FPS
1326 frames in 5.0 seconds = 264.989 FPS
1311 frames in 5.0 seconds = 261.782 FPS
706 frames in 5.0 seconds = 141.088 FPS
716 frames in 5.0 seconds = 143.086 FPS
725 frames in 5.0 seconds = 144.999 FPS
715 frames in 5.0 seconds = 142.888 FPS
720 frames in 5.0 seconds = 143.771 FPS
687 frames in 5.0 seconds = 137.291 FPS

thats what i get. i'm using the fglrx driver

I followed this to setup:
[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

made it a bit harder that i didn't have an xserver :( but i gots the xserver up.

cmaster@cmaster32bit-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1300 Series
OpenGL version string: 2.0.6334 (8.34.8)

these are the results i got from fgl_glxgears as well:
cmaster@cmaster32bit-desktop:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
893 frames in 5.0 seconds = 178.600 FPS
1622 frames in 5.0 seconds = 324.400 FPS
2118 frames in 5.0 seconds = 423.600 FPS
1952 frames in 5.0 seconds = 390.400 FPS
2019 frames in 5.0 seconds = 403.800 FPS
2188 frames in 5.0 seconds = 437.600 FPS
2187 frames in 5.0 seconds = 437.400 FPS
2185 frames in 5.0 seconds = 437.000 FPS
2186 frames in 5.0 seconds = 437.200 FPS
2185 frames in 5.0 seconds = 437.000 FPS
1890 frames in 5.0 seconds = 378.000 FPS
2180 frames in 5.0 seconds = 436.000 FPS
2191 frames in 5.0 seconds = 438.200 FPS
2112 frames in 5.0 seconds = 422.400 FPS

and fgl_glxgears is supposed to be more entensive for cpu and graphics. so why am i getting double the fps on that than on glxgears?

can you explain how you installed your drivers?
Then i might be able to get it going better the same way.

I'm looking at the official ati installer right now. I'm not really sure if i want to touch it but if it doesnt work some other way then i guess i'll have to.

A summary of how i installed it:
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial /etc/X11/xorg.conf
sudo aticonfig --overlay-type=Xv

I'm just gona go try rtcw again. Just in case.

Maybe i should be installing fglrx-control and fglrx-kernel-source?

---

### Post by nzadLithium on 2007-09-11
any idea's people?

---

