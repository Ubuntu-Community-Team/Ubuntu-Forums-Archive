---
title: "A Benchmark Tool"
date: 2006-03-16
forum: Gaming &amp; Leisure
---

### Post by Perfect Storm on 2006-03-16
Here's the howto build GL O.B.S: [http://gaming.gwos.org/index.php?option=com_content&task=view&id=27&Itemid=63](http://gaming.gwos.org/index.php?option=com_content&task=view&id=27&Itemid=63)

As we know that glxgears isn't a benchmark tool, I found this

[GL O.B.S.]("http://globs.sourceforge.net/")

It seems promising and done some test with it

Graphic card: GF 5200 128 mb
Test Width: 640 Height 480
Time: 5 sec.

GL Pointz: 367.6 fps
GL Shadow: 139.8 fps
GL blit: 411.0 fps
Fake: 346244.4 fps (without displaying anything)
GL blit ext: 398.2 fps
GL smoke: 218.0  fps

---

### Post by Greg2 on 2006-03-16
This does seem very promising... and appears to work very well. Now I can compare the different driver modules and memory allocations for my systems.

Thanks for the info.

---

### Post by e2k on 2006-03-16
Indeed, have to give it a shot \\:D/

---

### Post by scott_kirkwood on 2006-06-20
GeForce FX 5600
Intel Pentium 4 2.4 GHz 1 Gig RAM 512 Cache
$ cat /proc/version
Linux version 2.6.15-25-686 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP PREEMPT Wed Jun 14 11:34:19 UTC 2006

GL_pointz   352.2
GL_Shadow 300.0
GL_blit       544.4
Fake          350283.0
GL_blit_ext 515.4
GL_smoke   294.8

---

### Post by Perfect Storm on 2006-06-21
For those who don't know howto compile'n'install' it I wrote a howto: [http://gaming.gwos.org/index.php?option=com_content&task=view&id=27&Itemid=63](http://gaming.gwos.org/index.php?option=com_content&task=view&id=27&Itemid=63)

---

### Post by Starmartyr on 2006-07-02
XFX Geforce 7900 GT Extreme 520Mhz 256 PCI-Express with AMD Athlon 64 3700

GL_pointz 1383.8
GL_Shadow 0 - wouldn't initiate
GL_blit 6056.4
Fake 186491.4
GL_blit_ext 6182.4
GL_smoke 1345.4

---

### Post by patrick295767 on 2006-07-03
Very good program  :D 
(I'll give a try too)

Is there any program like sisoft sandra benchmark to check speed of our pc ?
([http://active-hardware.com/english/misc/sandra.html](http://active-hardware.com/english/misc/sandra.html))

Thank you for ur great contribution to this forum !!

---

### Post by lotheac on 2006-07-03
Geforce 6600 GT, Athlon 64 3500+. 640x480, 5sec tests.

GL_pointz 1325.4
GL_shadow 1926.4
GL_blit 2535.8
Fake 7560028.0
GL_blit_ext 2518.6
GL_smoke 1250.8

;)

---

### Post by EReckase on 2006-07-03
HP Pavilion dv8000, (Turion running 32-bit Dapper) ATI Radeon Xpress 200M, 8.24.8 drivers:

GL_pointz 184.8
GL_shadow 234.6
GL_blit 521.0
GL_smoke 148.6

---

### Post by Perfect Storm on 2006-07-03
[QUOTE=patrick295767]Very good program  :D 
(I'll give a try too)

Is there any program like sisoft sandra benchmark to check speed of our pc ?
([http://active-hardware.com/english/misc/sandra.html](http://active-hardware.com/english/misc/sandra.html))

Thank you for ur great contribution to this forum !![/QUOTE]


Thanks, Patrick :) 
Not what I know off.


My GT6600 256 mb on P4 2.4ghz 1024mb 800mhz ram.

640x480 5 secs.:

GL Pointz: 1074.6
GL blit: 2161.0
Fake: 331189.4
GL blit ext: 2147.0
GL smoke: 974.0

---

### Post by Megatog615 on 2006-07-04
```
$ sudo scons
Password:
scons: Reading SConscript files ...
sh: sdl-config: command not found
sh: sdl-config: command not found
:: Checking for libs
Checking for SDL_Init(SDL_INIT_VIDEO) in C library libSDL... no
Did not find libSDL, exiting!

```Help? I have libSDL installed...

---

### Post by Perfect Storm on 2006-07-04
[QUOTE=Megatog615]```
$ sudo scons
Password:
scons: Reading SConscript files ...
sh: sdl-config: command not found
sh: sdl-config: command not found
:: Checking for libs
Checking for SDL_Init(SDL_INIT_VIDEO) in C library libSDL... no
Did not find libSDL, exiting!

```Help? I have libSDL installed...[/QUOTE]

Also libsdl1.2-dev libsdl-image1.2-dev and libsdl-gfx1.2-dev?

---

### Post by ubu_dynamite on 2006-08-24
GL_shadow
Could not parse benchmark output:
Unable to open cube.mtl Cannot load the object!

GL_blit_ext
OpenGL extension GL_ARB_texture_rectangle is missing!

GL_smoke   1.0  547.8     640|480
Fake       1.0  378899.2  640|480
GL_blit    1.0  1098.8    640|480
GL_pointz  1.0  395.4     640|480

Folowed this thread:
[http://gaming.gwos.org/index.php?option=com_content&task=view&id=27&Itemid=63](http://gaming.gwos.org/index.php?option=com_content&task=view&id=27&Itemid=63)

---

### Post by Perfect Storm on 2006-08-24
Aye, that's a newer one I wrote. I'll add the link to the first post then.

---

### Post by OffHand on 2006-10-16
I am trying to install this application but I have some dependency problems. I am using Edgy.

```

$ sudo aptitude install libsdl-image1.2-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  libglu1-mesa-dev 
The following NEW packages will be automatically installed:
  libaa1-dev libartsc0-dev libaudio-dev libdirectfb-dev libdirectfb-extra 
  libesd0-dev libjpeg62-dev libncurses5-dev libsdl1.2-dev libslang2-dev 
  libtiff4-dev libtiffxx0c2 
The following packages have been kept back:
  python-egenix-mxproxy python-egenix-mxstack python-egenix-mxtexttools 
The following NEW packages will be installed:
  libaa1-dev libartsc0-dev libaudio-dev libdirectfb-dev libdirectfb-extra 
  libesd0-dev libjpeg62-dev libncurses5-dev libsdl-image1.2-dev 
  libsdl1.2-dev libslang2-dev libtiff4-dev libtiffxx0c2 
0 packages upgraded, 14 newly installed, 0 to remove and 3 not upgraded.
Need to get 4579kB of archives. After unpacking 17.7MB will be used.
The following packages have unmet dependencies:
  libglu1-mesa-dev: Depends: libglu1-mesa (= 6.5.1~20060817-0ubuntu3) but 6.5.1+cvs20060824 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Downgrade the following packages:
libglu1-mesa [6.5.1+cvs20060824 (now) -> 6.5.1~20060817-0ubuntu3 (edgy)]

Score is -42

Accept this solution? [Y/n/q/?] q
```

---

### Post by dannyboy79 on 2006-10-16
> **Starmartyr said:**
> XFX Geforce 7900 GT Extreme 520Mhz 256 PCI-Express with AMD Athlon 64 3700

GL_pointz 1383.8
GL_Shadow 0 - wouldn't initiate
GL_blit 6056.4
Fake 186491.4
GL_blit_ext 6182.4
GL_smoke 1345.4

something looks really wrong with this guys "fake" test, another person that didn't even have this good of a card had like 7 million, where this card is at only 186,00 and you can see that his GL_Shadow didn't even work??? I would look into this if I were you. I'll post my GeForce 6200 results when i get home.

---

### Post by Perfect Storm on 2006-10-16
I havn't tested it on edgy yet, but from what I've seen of your output is that it can be of 2 reasons, 1) the dependency is borked 2) You have some unofficial source in your sourcelist.

---

### Post by Perfect Storm on 2006-10-18
I've completly rewritten the how on ubuntuforums (so it looks like the one at Ubuntu gamers arena): [http://ubuntuforums.org/showthread.php?t=157429](http://ubuntuforums.org/showthread.php?t=157429)

It have been tested on Edgy with beryl and latest 9xxx nvidia driver.

---

### Post by testbenchdude on 2006-12-09
Can you all please list the resolution you tried this on? I entered 1280 x 1024 in order to fullscreen my LCD. Here's my results (fps **bolded**):

2 7900GT's in SLI
C2D 6600
2gb 800MHz DDR2

GL_shadow|1.0|**1165.0**|1280|1024|True|2006-12-09 00:12:00
GL_pointz|1.0|**2542.8**|1280|1024|True|2006-12-09 00:12:08
GL_blit|1.0|**3777.8**|1280|1024|True|2006-12-09 00:12:16
Fake|1.0|**876703.0**|1280|1024|True|2006-12-09 00:12:23
GL_blit_ext DNR
GL_smoke|1.0|**917.6**|1280|1024|True|2006-12-09 00:12:34

Cant run the fifth one for some reason...

---

