---
title: "Flightgear is tooo slooooow!"
date: 2007-07-18
forum: Gaming &amp; Leisure
---

### Post by Keith_Beef on 2007-07-18
And I can't figure out why!

Look at these figures:

```

cat /proc/cpuinfo 
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 6
model           : 10
model name      : AMD Athlon(tm) XP 2600+
stepping        : 0
cpu MHz         : 1913.245
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow ts
bogomips        : 3829.27
clflush size    : 32

lspci -v
03:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV200 QW [Radeon 7500] (prog-if 00 [VGA])
        Subsystem: C.P. Technology Co. Ltd RV200 QW [Radeon 7500 Evil Master Multi Display Edition]
        Flags: bus master, stepping, 66MHz, medium devsel, latency 32, IRQ 22
        Memory at d0000000 (32-bit, prefetchable) [size=128M]
        I/O ports at c000 [size=256]
        Memory at df000000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at de000000 [disabled] [size=128K]
        Capabilities: <access denied>

glxgears -info
GL_RENDERER   = Mesa DRI Radeon 20061018 AGP 1x x86/MMX+/3DNow!+/SSE TCL
GL_VERSION    = 1.3 Mesa 6.5.2
GL_VENDOR     = Tungsten Graphics, Inc.
GL_EXTENSIONS = GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_logic_op GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_compiled_vertex_array GL_EXT_convolution GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_histogram GL_EXT_packed_pixels GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_APPLE_packed_pixels GL_ATI_texture_env_combine3 GL_ATI_texture_mirror_once GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_MESA_ycbcr_texture GL_MESA_window_pos GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texture_rectangle GL_NV_texgen_reflection GL_OES_read_format GL_SGI_color_matrix GL_SGI_color_table GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod
6942 frames in 5.0 seconds = 1388.353 FPS
6918 frames in 5.0 seconds = 1383.565 FPS
6943 frames in 5.0 seconds = 1388.555 FPS

glxgears -fullscreen -info
GL_RENDERER   = Mesa DRI Radeon 20061018 AGP 1x x86/MMX+/3DNow!+/SSE TCL
GL_VERSION    = 1.3 Mesa 6.5.2
GL_VENDOR     = Tungsten Graphics, Inc.
GL_EXTENSIONS = GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_logic_op GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_compiled_vertex_array GL_EXT_convolution GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_histogram GL_EXT_packed_pixels GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_APPLE_packed_pixels GL_ATI_texture_env_combine3 GL_ATI_texture_mirror_once GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_MESA_ycbcr_texture GL_MESA_window_pos GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texture_rectangle GL_NV_texgen_reflection GL_OES_read_format GL_SGI_color_matrix GL_SGI_color_table GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod
599 frames in 5.0 seconds = 119.792 FPS
597 frames in 5.0 seconds = 119.275 FPS
597 frames in 5.0 seconds = 119.276 FPS

xdpyinfo
name of display:    :0.0
version number:    11.0
vendor string:    The X.Org Foundation
vendor release number:    70200000
X.Org version: 7.2.0
maximum request size:  16777212 bytes
motion buffer size:  256
bitmap unit, bit order, padding:    32, LSBFirst, 32
image byte order:    LSBFirst
number of supported pixmap formats:    7
supported pixmap formats:
    depth 1, bits_per_pixel 1, scanline_pad 32
    depth 4, bits_per_pixel 8, scanline_pad 32
    depth 8, bits_per_pixel 8, scanline_pad 32
    depth 15, bits_per_pixel 16, scanline_pad 32
    depth 16, bits_per_pixel 16, scanline_pad 32
    depth 24, bits_per_pixel 32, scanline_pad 32
    depth 32, bits_per_pixel 32, scanline_pad 32
keycode range:    minimum 8, maximum 255
focus:  window 0x1800022, revert to Parent
number of extensions:    30
    BIG-REQUESTS
    Composite
    DAMAGE
    DPMS
    Extended-Visual-Information
    GLX
    MIT-SCREEN-SAVER
    MIT-SHM
    MIT-SUNDRY-NONSTANDARD
    RANDR
    RENDER
    SECURITY
    SGI-GLX
    SHAPE
    SYNC
    TOG-CUP
    X-Resource
    XAccessControlExtension
    XC-APPGROUP
    XC-MISC
    XFIXES
    XFree86-Bigfont
    XFree86-DGA
    XFree86-DRI
    XFree86-Misc
    XFree86-VidModeExtension
    XInputExtension
    XKEYBOARD
    XTEST
    XVideo

```

And yet FlightGear runs at only 1 frame per second! That doesn't change, whether I run it in a small window, or full screen. What's going on, here?


Beef.

---

### Post by jusmurph on 2007-07-18
You tried turing the graphix down?
Ignore screen size... I'm talking resolution, draw distance, anti alaising etc.

btw... not being rude but your computer is average, its not a gaming powerhouse.

---

### Post by Keith_Beef on 2007-07-19
I know it's not a racehorse, but I built it about three years ago to be a general purpose, inexpensive computer. As things go, it does its job well.

I tried changing the whole screen resolution, even tried turning off most of the textures and objects, and I still only get 1 fps.

But a strange thing happens when I run glxgears at the same time as FlightGear... I get more frames per second, but the display becomes somewhat corrupted so I can no longer read the framerate. But it is playable, and feels like it may well be around 20 fps.

Beef

---

### Post by weblordpepe on 2007-07-19
Are you using an ATI card?
What does **fglrxinfo** say?

---

### Post by Keith_Beef on 2007-07-20
> **weblordpepe said:**
> Are you using an ATI card?
What does **fglrxinfo** say?

Yes, it's an ATI Radeon 7500 (look in my original post, for the output from lspci -v.

From memory (not at that machine at the moment), I listed the loaded kernel modules before and while running glxgears, and no new modules were loaded.

The video driver used is radeon, not fglrx.

Beef.

---

### Post by Keith_Beef on 2007-07-23
Well, after trying to follow [these]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-796aa4d6d0477c8ed722acef1878cc5626855ae3-2") instructions to instal the binary ATI driver, the situation is sort of worse...

Sort of, because FlightGear now runs at 1 frame per second all the time, without the speed-up to 25 fps that I got by running glxgears at the same time... but without the display corruption.

I followed those instructions, but when I started X I got a message about there being no screens defined. I tried to fix the xorg.conf file, but that didn't help things much. I.e. I was still stuck with the radeon driver and 1 fps, even though there was a line in that file to specify the fglrx driver.

The "restricted drivers manager" only ever listed the "Lucere Agere linmodem controller driver", never any ATI driver.

Beef.

---

### Post by Zannax on 2007-07-24
> **Keith_Beef said:**
> Well, after trying to follow [these]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-796aa4d6d0477c8ed722acef1878cc5626855ae3-2") instructions to instal the binary ATI driver, the situation is sort of worse...



Sure: that's perfectly normal because ATI proprietary driver does'nt support your card at all.

ATI has begun to support us Linux users only from Radeon 8500 and above (if I rember well), so you can't install ATI binary driver and that's why the restricted d. manager doesn't list it at all...

I know that well because I have a Radeon 7000 myself... :-)

---

### Post by Keith_Beef on 2007-07-24
> **Zannax said:**
> Sure: that's perfectly normal because ATI proprietary driver does'nt support your card at all.

ATI has begun to support us Linux users only from Radeon 8500 and above (if I rember well), so you can't install ATI binary driver and that's why the restricted d. manager doesn't list it at all...

I know that well because I have a Radeon 7000 myself... :-)

Thanks a lot, Zannax!

If you hadn't pointed that out to me, I don't know how long it would have taken me before reading that first paragraph in the HowTo:

> [LIST]
[*]The model of the card is in the 9xxx series, 9500 or higher, or it is in the X series (e.g. X300), or it has TV-Out capability. The 'fglrx' driver does not support cards earlier than the 9500.
[/LIST]

So I followed a link from that page to another [HowTo]("https://help.ubuntu.com/community/RadeonDriver#head-93fc0a86162afbf71a5b84eff7da6c6a338656b1") that helped me to get rid of the superfluous fglrx stuff and get back to the correct version of Mesa.

I now see: 
```
$ glxinfo |grep vendor
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Tungsten Graphics, Inc.
```

I also tweaked xorg.conf as advised in the Radeon driver HowTo:

```
Section "Device"
        Identifier      "Radeon 9600"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option          "XAANoOffscreenPixmaps"
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection

Section "ServerLayout"
        Option          "AIGLX"         "true"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection
```

Still down to 1 fps, or around 25 to 30 fps if I run glxgears at the same time, with the corruption in the FlightGear window. :confused:  :( :mad:

I can just about fly and land the Northrop A-10, despite the corrupted display meaning that I have almost no instruments, and little scenery to help. 

This is so puzzling, and so infuriating. A yoke and rudderset should arrive this afternoon, and I'd hoped to get this sorted out before.

Looks like I'm in the market for a new card, then...

From a personal, ethical point of view, I would prefer to use Free drivers. Are there any video cards that are capable of 30 fps or better without resorting to a proprietary driver?

Beef.

---

### Post by Zannax on 2007-07-24
> **Keith_Beef said:**
> Thanks a lot, Zannax!

If you hadn't pointed that out to me, I don't know how long it would have taken me before reading that first paragraph in the HowTo:



You're welcome. :-)

For the corrupted display, I've experienced it as well with some programs, but now it's gone after some tweaking:

I'm not so expert but you can try turning off some combination of "Composite", "AIGLX", "XAAN..."

i.e. try:
```
Section "Extensions"
        Option "Composite" **"Disable"**
EndSection
```

because at least in my case it's turned on by default.
That solved more than one issue for me, including display corruption and freezing...
On the other hand, you lose desktop-effects too with that.

For the best brand of video-card I don't know but I'd check:

[https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)

first of all...

---

### Post by Keith_Beef on 2007-07-24
So, I can get flight ger up to around 25 to 30 frames per second, but only if I run glxgears at the same time.

The trouble is, that doing that corrupts the display of the Flight Gear window.

The scenery (and the plane, if I use a view like chase or helicopter) gets made from textures that look like bitmaps of the instrument panel, and the instrument panel is a mess.

I've tried a variety of options and settings in xorg.conf and I've created a ~/.drirc file.

```
<driconf>
        <device screen="0" driver="radeon">
                <application name="all">
                        <option name="allow_large_textures" value="2" />
                </application>
        </device>
</driconf>
```

```
$ glxinfo |grep vendor
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Tungsten Graphics, Inc.
```


Glxgears gives me a good frame rate:

```
$ glxgears -info
GL_RENDERER   = Mesa DRI Radeon 20061018 AGP 2x x86/MMX+/3DNow!+/SSE TCL
GL_VERSION    = 1.3 Mesa 6.5.2
GL_VENDOR     = Tungsten Graphics, Inc.
GL_EXTENSIONS = GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_logic_op GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_compiled_vertex_array GL_EXT_convolution GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_histogram GL_EXT_packed_pixels GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_APPLE_packed_pixels GL_ATI_texture_env_combine3 GL_ATI_texture_mirror_once GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_MESA_ycbcr_texture GL_MESA_window_pos GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texture_rectangle GL_NV_texgen_reflection GL_OES_read_format GL_SGI_color_matrix GL_SGI_color_table GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod
6563 frames in 5.0 seconds = 1312.597 FPS
6513 frames in 5.0 seconds = 1302.564 FPS
7139 frames in 5.0 seconds = 1427.631 FPS
7137 frames in 5.0 seconds = 1427.383 FPS
7124 frames in 5.0 seconds = 1424.639 FPS
7127 frames in 5.0 seconds = 1425.275 FPS
```

I just can't understand why:
[LIST]
[*]running Flight gear alone gives only 1 fps, but with glxgears running at the same time I get 25 to 30 fps
[*]running glxgears corrupts the Flight gear display.
[/LIST]

I just downloaded bzflag, and had a quick play. That works just fine. No problems with corruption or with frame rate... :confused:

Beef

---

### Post by Keith_Beef on 2007-07-27
Well, last night I recovered my original xorg.conf file and deleted the /etc/drirc file.

I ran FlightGear with --aircraft=A-10 and got my 1 fps, started glxgears and got a corrupted display but 30 fps.

I stopped glxgears.

Then I stopped FlightGear and started it again but with a different aircraft; the Cesna 172.

I couldn't get the frame rate to display (maybe this doesn't work when the aircraft has no HUD), but it seemed to be around 30 fps and perfectly playable!

I tried another simple plane, the J3Cub, and got similar performance: good framerate and a responsive plane, though it felt more sluggish than the Cesna.

So I tried the Lightning. This was like the A-10: unresponsive and slow framemrate.

The Lightning, the A-10 and the J3 are YaSim models.

The C-172 is an FBSim model.

I've not had enough time to try out more of the small planes, or to compare flight models, but maybe it is the complexity of the YaSim models for the big jet planes that was the cause of the slowness in the first place.


Beef.

---

### Post by visionary on 2008-01-13
Maybe you could try the following which i harvested from some other websites which helped me greatly with Flightgear in Gusty....

1)When you start flight gear, consider starting with the following options in your command.... (You can read more from here [http://mail.flightgear.org/pipermail/flightgear-users/2005-May/010980.html](http://mail.flightgear.org/pipermail/flightgear-users/2005-May/010980.html) )

> --control=mouse
> --disable-intro-music
> --disable-random-objects
> --disable-sound
> --disable-hud-3d
> --disable-specular-highlight
> --fog-fastest
> --model-hz=60
> --geometry=800x600
> --visibility=10000.0
> --fov=50
> 
> --prop:/sim/rendering/static-lod/detailed=500
> --prop:/sim/rendering/static-lod/rough=5000
> --prop:/sim/rendering/static-lod/bare=15000
> --prop:/environment/clouds/layer[1]/coverage="clear"
> --log-level=alert

That actually improved a little.....Now for the biggest improvement i go was to to do the following.....

2) downloaded driconf (sudo apt-get install driconf)

3)Then edit device section of /etc/X11/xorg.conf to show as

Section "Device"
Identifier "ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
Driver "ati"
[B]BusID "PCI:1:0:0"
Option "AGPMode" "4"
Option "EnablePageFlip" "true"
Option "AGPFastWrite" "true"
Option "EnableDepthMoves" "true"
Option "GARTSize" "64"
Option "AGPSize" "64"
Option "backingstore" "on"
Option "UseInternalAGPGART" "no"[/B]
EndSection


Though i am using Nvidia card, i added those lines (in bold)  in my xorg.conf file.

Now restart your system and enjoy your flight gear.
Hope that helps!

Cheers!

---

### Post by Sockerdrickan on 2008-01-13
lol ATi drivers :lolflag: might be better soon though with the new specs releasing all the time

---

### Post by foska on 2008-03-24
Will Flightgear run with a GeForce FX 5500 Graphics Card?  It is running very slowly now and I can really say that it is non-responsive.  I notice that most people are using ATI cards?

---

### Post by foska on 2008-03-25
I thought that I'd come back and give an update on my sojurn with FlightGear.

I realised that there is also a Windows Version so I installed it on my WinXP boot but surprise, surprise same problem. So I reasoned that it must be a driver issue.  I checked and there was a later NVidia driver for my graphics adapter and I installed it.  Flightgear works a lot better now just that I am having trouble with the controlling the planes with my keyboard.  NVIDIA does a linux driver for this graphics adapter so I think I'll try that next. I'll let you know how it works!

---

### Post by foska on 2008-03-28
Update.....

Well I pushed my luck trying to eek out more performance from my NVIDIA card.  At first I enabled the driver in the Restricted Drivers Manager.  That worked great! So i reckoned it could be better if I installed the latest driver from NVIDIA's website, which on the face of it, seemed to be a reasonable assumption.  That turned out to be a bad idea!  The driver installation went beautiful but after rebooting the O/S could not the screen resolution correct. I could not be bothered and just reinstalled the Ubuntu! (with the driver from the Restricted Driver Manager enabled!).

---

### Post by Sockerdrickan on 2008-03-28
You should have installed the drivers correctly instead. :lolflag:

anyway

```
GET DRIVER

sudo apt-get install linux-headers-`uname -r` build-essential xserver-xorg-dev

sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common linux-restricted-modules*

sudo rm /etc/init.d/nvidia-*

CTRL+ALT+F6+LOG ON TO YOUR UBUNTU ACCOUNT

sudo /etc/init.d/gdm stop

sudo sh NV (PRESS TAB TO GET THE REST)

GO THROUGH THE INSTALLATION

sudo /etc/init.d/gdm start
```

---

### Post by foska on 2008-03-31
Yeah it was after the "sudo /etc/init.d/gdm start" that all hell broke loose! Gutsy just could not figure out which graphics adapter was installed. No biggie its working great now. If I feel brave I may try it again.

---

