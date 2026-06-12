---
title: "Games installed through Ubuntu Software Centre not working"
date: 2010-06-04
forum: Gaming &amp; Leisure
---

### Post by Niknation on 2010-06-04
Hey guys
I recently downloaded Warsow and Tremulous from the Ubuntu Software Centre 
It seems to have fully downloaded and installed but when I 
click to run it in my games section nothing loads.
Anyone can help me with this?
Thanks

---

### Post by llawwehttam on 2010-06-04
what graphics card do you have and what drivers have you installed for it?

---

### Post by Bhamid on 2010-06-04
I have the same problem (both worked in 9.10), I have the 195 Nvidia drivers installed for a 9300 GE.

---

### Post by donkyhotay on 2010-06-04
as mentioned previously graphics drivers are most likely culprit for those games however try launching the games from CLI (terminal) and post the output to double check.

---

### Post by Niknation on 2010-06-04
> **llawwehttam said:**
> what graphics card do you have and what drivers have you installed for it?
Im using a ATI HD3870 with the ATI proprietary FGLRX driver.
When I run Tremulous from terminal this is what i get
```
/home/nikhil/.tremulous/base
/usr/share/games/tremulous/base/vms-1.1.0.pk3 (4 files)
/usr/share/games/tremulous/base/map-uncreation-1.1.0.pk3 (110 files)
/usr/share/games/tremulous/base/map-tremor-1.1.0.pk3 (45 files)
/usr/share/games/tremulous/base/map-transit-1.1.0.pk3 (135 files)
/usr/share/games/tremulous/base/map-niveus-1.1.0.pk3 (134 files)
/usr/share/games/tremulous/base/map-nexus6-1.1.0.pk3 (151 files)
/usr/share/games/tremulous/base/map-karith-1.1.0.pk3 (118 files)
/usr/share/games/tremulous/base/map-atcs-1.1.0.pk3 (87 files)
/usr/share/games/tremulous/base/map-arachnid2-1.1.0.pk3 (67 files)
/usr/share/games/tremulous/base/data-1.1.0.pk3 (1229 files)
/usr/share/games/tremulous/base
/usr/lib/tremulous/base

----------------------
2080 files in pk3 files
execing default.cfg
couldn't exec autogen.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----

------- Input Initialization -------
Joystick is not active.
------------------------------------
...loading libGL.so.1:
Calling SDL_Init(SDL_INIT_VIDEO)...
SDL_Init(SDL_INIT_VIDEO) passed.
Initializing OpenGL display
...setting mode 3: 640 480
Received signal 11, exiting...
----- CL_Shutdown -----
RE_Shutdown( 1 )
X Error of failed request:  BadLength (poly request too large or internal Xlib length error)
  Major opcode of failed request:  65 (X_PolyLine)
  Serial number of failed request:  13
  Current serial number in output stream:  14
```and when I run Warsow I get this
```
nikhil@ubuntu:/usr/games$ ./warsow
Added pk3 file /usr/share/games/warsow/basewsw/data0_05.pk3 (1090 files)
Added pk3 file /usr/share/games/warsow/basewsw/data0_05pure.pk3 (1331 files)
Added pk3 file /usr/share/games/warsow/basewsw/editortextures.pk3 (20 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wamphi1.pk3 (2 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wamphi2.pk3 (2 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wbomb1.pk3 (2 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wbomb2.pk3 (2 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wca1.pk3 (2 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wca2.pk3 (2 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wca3.pk3 (2 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wctf1.pk3 (2 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wctf2.pk3 (2 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wctf3.pk3 (2 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wctf4.pk3 (2 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wctf5.pk3 (2 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wctf6.pk3 (2 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wdm1.pk3 (2 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wdm10.pk3 (2 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wdm11.pk3 (2 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wdm12.pk3 (2 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wdm13.pk3 (2 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wdm14.pk3 (2 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wdm15.pk3 (2 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wdm16.pk3 (2 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wdm17.pk3 (4 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wdm18.pk3 (2 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wdm19.pk3 (2 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wdm2.pk3 (2 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wdm20.pk3 (2 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wdm3.pk3 (2 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wdm4.pk3 (2 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wdm5.pk3 (2 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wdm6.pk3 (2 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wdm7.pk3 (2 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wdm8.pk3 (2 files)
Added pk3 file /usr/share/games/warsow/basewsw/map_wdm9.pk3 (2 files)
Added pk3 file /usr/share/games/warsow/basewsw/models_nate.pk3 (22 files)
Added pk3 file /usr/share/games/warsow/basewsw/modules_05.pk3 (16 files)
Added pk3 file /usr/share/games/warsow/basewsw/tex_36.pk3 (28 files)
Added pk3 file /usr/share/games/warsow/basewsw/tex_baxandall.pk3 (35 files)
Added pk3 file /usr/share/games/warsow/basewsw/tex_billboard.pk3 (14 files)
Added pk3 file /usr/share/games/warsow/basewsw/tex_blx.pk3 (328 files)
Added pk3 file /usr/share/games/warsow/basewsw/tex_blxbis.pk3 (112 files)
Added pk3 file /usr/share/games/warsow/basewsw/tex_cha0swsw.pk3 (90 files)
Added pk3 file /usr/share/games/warsow/basewsw/tex_ecel.pk3 (197 files)
Added pk3 file /usr/share/games/warsow/basewsw/tex_etr.pk3 (6 files)
Added pk3 file /usr/share/games/warsow/basewsw/tex_exwsw.pk3 (185 files)
Added pk3 file /usr/share/games/warsow/basewsw/tex_factory.pk3 (88 files)
Added pk3 file /usr/share/games/warsow/basewsw/tex_fakeads.pk3 (17 files)
Added pk3 file /usr/share/games/warsow/basewsw/tex_format.pk3 (22 files)
Added pk3 file /usr/share/games/warsow/basewsw/tex_hazelh.pk3 (92 files)
Added pk3 file /usr/share/games/warsow/basewsw/tex_hexagons.pk3 (47 files)
Added pk3 file /usr/share/games/warsow/basewsw/tex_jewels.pk3 (8 files)
Added pk3 file /usr/share/games/warsow/basewsw/tex_melee.pk3 (12 files)
Added pk3 file /usr/share/games/warsow/basewsw/tex_nature.pk3 (7 files)
Added pk3 file /usr/share/games/warsow/basewsw/tex_refly.pk3 (48 files)
Added pk3 file /usr/share/games/warsow/basewsw/tex_russus.pk3 (9 files)
Added pk3 file /usr/share/games/warsow/basewsw/tex_solidfake.pk3 (8 files)
Added pk3 file /usr/share/games/warsow/basewsw/tex_supersymmetry.pk3 (15 files)
Added pk3 file /usr/share/games/warsow/basewsw/tex_terrain.pk3 (8 files)
Added pk3 file /usr/share/games/warsow/basewsw/tex_wsw_adverts.pk3 (61 files)
Added pk3 file /usr/share/games/warsow/basewsw/tex_wsw_cave1.pk3 (25 files)
Added pk3 file /usr/share/games/warsow/basewsw/tex_wsw_city1.pk3 (138 files)
Added pk3 file /usr/share/games/warsow/basewsw/tex_wsw_flareshalos.pk3 (21 files)
Added pk3 file /usr/share/games/warsow/basewsw/tex_zone_neutre.pk3 (9 files)
Using /home/nikhil/.warsow-0.5 for writing
Executing: default.cfg
Couldn't execute: config.cfg
Couldn't execute: autoexec.cfg
fs_basepath is write protected.
fs_usehomedir is write protected.
Hostname: ubuntu.ubuntu-domain
Alias: ubuntu
IP: 127.0.1.1
------- angel script initialization -------
Loading angelwrap module.
Loading angelwrap failed
Game running at 62 fps. Server transmit at 20 pps
Console initialized.

----- R_Init -----
Using libGL.so.1 for OpenGL...Display initialization
..XFree86-VidMode Extension Version 2.2
..XFree86-Xinerama Extension Version 1.1
********************
ERROR: Received signal 11

********************
Error: Received signal 11

```

---

### Post by Niknation on 2010-06-05
Bump please people I need some help...

---

### Post by cgroza on 2010-10-15
This is what I got for signal 11: 



On  POSIX-compliant platforms, SIGSEGV is the signal sent to a process when  it makes an invalid memory reference, or segmentation fault. The  symbolic constant for SIGSEGV is defined in the header file signal.h. ..

---

### Post by Shazzner on 2010-10-15
Take a look at this:
[http://www.ubuntugamer.com/2010/10/how-to-install-the-latest-proprietary-graphics-driver-in-ubuntu/](http://www.ubuntugamer.com/2010/10/how-to-install-the-latest-proprietary-graphics-driver-in-ubuntu/)

Try updating and report back, it's most likely a driver issue.

When it comes to games running improperly there are three main culprits:
- Graphics Drivers
- Sound
- Out of date libraries (not an issue if installing from the software center)

Edit: oh this is an old thread, why was it bumped?

---

