---
title: "Compiz: no rendering present"
date: 2009-12-23
forum: Desktop Environments
---

### Post by lkarydas on 2009-12-23
Hi,
I am trying to set up my new Dell Inspiron 537s to run compiz on Ubuntu 9.10.
My graphics card is ATI HD 4350. I have the latest drivers from ATI website. When I turn on compiz I have no direct rendering. Also compiz-check says that I have no rendering present:
```
 Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME

 Graphics chip:         ATI Technologies Inc RV710 [Radeon HD 4350]
 Driver in use:         fglrx
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 

```I guess the rendering mode should be AIGLX.
The output of cat /var/log/Xorg.0.log | grep '(WW)' is:
```
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) Falling back to old probe method for fglrx
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(WW) fglrx(0): could not detect X server version (query_status=-1)
(WW) fglrx(0): Option "AccelMethod" is not used
(WW) fglrx(0): Option "EnableDepthMoves" is not used
(WW) fglrx(0): Option "VideoOverlay" is not used
```I tried to find a solution for the "falling back to old probe method for fglrx" and the "no matching device section" but with no luck. Does anybody know if this is causing the problem?

My xorg.conf looks like this:

```
Section "ServerLayout"
    Identifier     "amdcccle Layout"
    Screen      0  "amdcccle-Screen[1]-0" 0 0
    Option "AIGLX" "True"
EndSection

Section "Files"
EndSection

Section "Module"
    Load  "glx"
    Load  "dri"
EndSection

Section "Monitor"
    Identifier   "Configured Monitor"
EndSection

Section "Monitor"
    Identifier   "0-DFP5"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1152x648"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Device"
    Identifier  "amdcccle-Device[1]-0"
    Driver      "fglrx"
    Option      "AccelMethod" "EXA"
    Option      "XAANoOffscreenPixmaps" "True"
        Option      "EnableDepthMoves"      "on"
        Option      "VideoOverlay"          "on"
    Option      "TexturedVideo" "True"
    Option         "TexturedVideoSync" "True" 
    Option        "Monitor-DFP5" "0-DFP5"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "Default Screen"
    Device     "Configured Video Device"
    Monitor    "Configured Monitor"
    DefaultDepth     24
EndSection

Section "Screen"
    Identifier "amdcccle-Screen[1]-0"
    Device     "amdcccle-Device[1]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "DRI"
    Mode 0666
EndSection

Section "ServerFlags"
    Option "AIGLX" "true"
EndSection

Section "Extensions"
    Option "RENDER" "Enable"
    Option "DAMAGE" "Enable"
    Option "Composite" "Enable"
    Option "XVideo" "Enable"
EndSection

```When I am not running compiz glxinfo reports yes for direct rendering but when I start compiz this turns to no.

Also, when I start compiz with:

```
compiz --replace ccp & emerald --replace &
```I get

```
Checking for Xgl: not present.
```Can anybody help?

---

### Post by gh4ever on 2009-12-24
I have the same bug.
I just switching from Ubuntu on one computer to a new computer with Mint. I was originally getting a software rasterizor not present error, but after messing with some stuff, I'm coming up with this error after running compiz-check.
Thanks in advance.

---

### Post by Dain1234 on 2010-02-14
I have the same problem:

I have an ATI Mobility HD 4330 Ubuntu 9.10, 2.6.31-19-generic . I downloaded the fglrx drivers over the repos. 3D seems to work (glxgears, google earth) pretty good. Only compiz doesn't want my system...

glxinfo:

```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: ATI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group
client glx vendor string: ATI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_create_context, GLX_ARB_get_proc_address, GLX_ARB_multisample, 
    GLX_EXT_import_context, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_MESA_allocate_memory, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_NV_swap_group, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_swap_barrier, GLX_SGIX_swap_group, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap, GLX_EXT_framebuffer_sRGB, 
    GLX_ARB_fbconfig_float
GLX version: 1.4
GLX extensions:
    GLX_ARB_create_context, GLX_ARB_get_proc_address, GLX_ARB_multisample, 
    GLX_EXT_import_context, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_MESA_swap_control, GLX_NV_swap_group, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_swap_barrier, GLX_SGIX_swap_group, GLX_SGIX_visual_select_group
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 4300 Series
OpenGL version string: 2.1.9016
OpenGL shading language version string: 1.40

```

compiz --replace
```

Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1366x768) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
Usage: /usr/bin/compiz.real

```compiz-check:

```
Gathering information about your system...

 Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc M92 LP [Mobility Radeon HD 4300 Series]
 Driver in use:         fglrx
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 


```xorg.conf
```
Section "Screen"
        Identifier      "Default Screen"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Default Device"
        Driver  "fglrx"
        Option      "XAANoOffscreenPixmaps" "true"
        Option      "EnableDepthMoves"      "on"
        Option      "VideoOverlay"          "on"
        Option      "TexturedVideo"         "True" 
        Option      "TexturedVideoSync"     "True"

EndSection

Section "DRI"
    Mode 0666
EndSection

Section "ServerFlags"
    Option "AIGLX" "true"
EndSection

Section "Extensions"
Option "Composite" "Enable"
EndSection

```

---

### Post by imiunleashed on 2010-05-01
I am facing the same prob on a ATI 4530 :(
Let me know the solution if you know it :)

---

### Post by still learning on 2010-05-05
I am having the exact same problem with the ATI 5770 card, has any one found a fix for this yet. I have been searching since 10.04 come out.



Gathering information about your system...

 Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Juniper [Radeon HD 5700 Series]
 Driver in use:         fglrx
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia)

---

### Post by 2Stoned on 2010-05-07
I got the same problem with my ATI Radeon HD2600 Pro. Seems that ATI has some issues with compiz:mad: And i have heard they dropped support for some 'older' ATI cards. But was anybody enable to fix this issue and run compiz with no problems on a ATI card?

---

### Post by asai on 2010-05-16
I have the same problem. My graphics card is ATI Radeon HD3650.
If anyone have a solution for this, please post. :confused:

---

### Post by body on 2010-06-02
Same for me (I am also on a Dell box)

compiz-check :

 Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RV630 [Radeon HD 2600XT]
 Driver in use:         fglrx
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia)

---

### Post by kwbbpc on 2010-06-10
Same sad situation.

No rendering method in use.

ATI Radeon HD3450

---

### Post by asai on 2010-06-30
Is there any news in this situation?

---

### Post by Jaygo333 on 2010-07-13
bump. Any new fix to this.
--------------------------
Gathering information about your system...

 Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RV770 [Radeon HD 4850]
 Driver in use:         fglrx
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 
---------------------------

---

### Post by mildlyAmused on 2010-07-13
I have a Radeon x1300, and for several weeks I've tested various versions of the xserver. Just to see which is the most stable / compatible with the fglrx.  

It seems the source packages associated with Xorg 7.4, fits the fglrx driver best. Atleast for Catalsyt 9.3. 

I think this is because Xorg 7.4 is just new enough, to include the core changes that improved the server, but not so new that it confuses the ATI/AMD driver.  
But even with my own /usr/xorg74 compiled,linked and ready to go, getting fglrx into Ubuntu 10.0.4 has already taken days out of my life. Missing symbol here, patch there.


In the long haul, it might just be better to trade/buy a new card until AMD gets their act together.

---

### Post by domel07 on 2010-08-04
Same here, ATI Radeon 5700, compiz does not work.

---

### Post by ashokmkd on 2010-08-04
To all ATI users.
Have you tried this command "aticonfig"
It solved the problem for me.

---

### Post by domel07 on 2010-08-04
Excellent hint. I managed now to get compiz running. But I see a lot of artifacts, mostly white outs. Any more hints?
Thanks,
Dominik

---

### Post by domel07 on 2010-08-04
...and a lot of keayboard shortcuts like ALT+F2 or ALT+TAB no longer work. But the effects (e.g. negative) are there.

---

### Post by domel07 on 2010-08-07
OK, all fine.
Use aticonfig to create an xorg.conf
Go to the compiz configuration, enable gnome support, enable window switching.
Some effects are broken though (white screen, artifacts, etc.).

---

### Post by asai on 2010-08-07
> **domel07 said:**
> Use aticonfig to create an xorg.conf
Do you have an example on the command?

---

### Post by ashokmkd on 2010-08-11
When i tried aticonfig, it really worked fine for me.
May be you should try removing that opensource ati drivers provided by ubuntu. These problems started when they started shipping these drivers. Upto 9.10, it worked fine. All i had to do was to download and install drivers.

---

### Post by sidtj on 2010-09-05
Hello

I had a similar problem but i was able to solve it...
I have a ATI Mobility Radeon HD 3650 in my toshiba sattelite with ubuntu 10.04.
My ubuntu had already compiz pre-installed... i installed the ATI drivers in SYSTEM > ADMIN > Hardware Drivers. Ok.
But i was getting the same problem when i tryed ./compiz-check: NO RENDERING METHOD although my ATI was ok and compiz too (but no compiz-fusion).

So, i installed ccsm through APPLICATIONS > UBUNTU CENTRAL OF PROGRAMS (search for ccsm). After installed, a new option is created in SYSTEM > ADMIN so that now you will be able to do some advanced adjusts in your compiz: so many animations, full control over everything in your screen! (you will continue seeing NO RENDERING if try compiz-check although!)

I dont know if someone is having exactly the same problem like me but, it could be useful. Sorry about any english error. I am brazillian and i am improving my english.

Thats all.

---

