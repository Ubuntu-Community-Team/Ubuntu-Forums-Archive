---
title: "Help Help Help (pl0x)~!"
date: 2007-01-10
forum: Gaming &amp; Leisure
---

### Post by Kingfield on 2007-01-10
Hey, when i try to run Regnum online it just closes, and in the eror log it gives this.. as an error

[GameClient][game_client.cpp(597)] Needed OpenGL extensions not found:

S3TC textures (GL_EXT_texture_compression_s3tc)
S3TC textures (GL_S3_s3tc)

I'm not sure if this is because i have a crappy graphics card, or is it because something isn't configured correctly or installed? 

Thanks in advance.

---

### Post by RomeReactor on 2007-01-10
Hi!
While we wait for someone more knowledgeable about this than i am let's find out if you have direct rendering enabled. Perhaps your problem has to do with this or not having your card's drivers up to date; then again, it may be that if your card is very old it doesn't support those extensions. In the terminal, try:

```
glxinfo | grep rendering
```

And let's see if those extensions are present (though not likely):

```
glxinfo | grep GL_EXT_texture_compression_s3tc
```

```
glxinfo | grep GL_S3_s3tc
```

Let's see what the output is. Also, post what card you have.

---

### Post by Kingfield on 2007-01-10
```
kingfield@kingfield-desktop:~$ glxinfo | grep rendering
direct rendering: Yes
kingfield@kingfield-desktop:~$ glxinfo | grep GL_EXT_texture_compression_s3tc
kingfield@kingfield-desktop:~$ glxinfo | grep GL_EXT_texture_compression_s3tc

```

The last two commands gave no output.

so i guess it doesn't work...? Btw, it is an S4 Savage card... I think it is really crap, coz if i set the colour to 24bit Direct rendering will not work.

---

### Post by RomeReactor on 2007-01-10
I'm not sure about this, but from the lack of output from the last two commands it may be that your card doesn't support those extensions. Try setting regnum to run on 16-bit color, if you haven't already, and let's see then...

---

### Post by RomeReactor on 2007-01-10
According to [these]("http://www.active-hardware.com/english/reviews/video/atc3970a.htm") [pages]("http://www.thetechzone.com/reviews/video/savage4/page2.htm"), your card does support the extensions. Try running glxgears:

```
glxgears -info
```

You should see a box with gears spinning. Sorry i can't be more helpful, but it's late here and i'm going to sleep. I'll be back tomorrow. Meanwhile, check out this [thread]("http://www.ubuntuforums.org/showthread.php?t=326128"), look at the bottom where it says "SOLVED". Hope this helps

---

### Post by Kingfield on 2007-01-10
```
GL_RENDERER   = Mesa DRI Savage4 20050829 AGP 1x
GL_VERSION    = 1.2 Mesa 6.4.1
GL_VENDOR     = S3 Graphics Inc.
GL_EXTENSIONS = GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_texture_compression GL_ARB_texture_env_add GL_ARB_texture_mirrored_repeat GL_ARB_transpose_matrix GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_compiled_vertex_array GL_EXT_convolution GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_histogram GL_EXT_packed_pixels GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_separate_specular_color GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_vertex_array GL_APPLE_packed_pixels GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_MESA_window_pos GL_NV_light_max_exponent GL_NV_texgen_reflection GL_OES_read_format GL_SGI_color_matrix GL_SGI_color_table GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod
```

well, tat sucks...

---

### Post by Kingfield on 2007-01-10
anything? and how to set regnum ro eun on 16bit colour

---

### Post by RomeReactor on 2007-01-11
When you run rolauncher, after you type your password and the screen with the two mages appears, you'll see below "Options" (or "Opciones", if it's in spanish). Click there to set the game to run on your desired resolution, but set it on 16-bit color, eg. 1024x768x**16**. In the Regnum forums your card's status is "unknown", which means the game may or may not run on it. Have you tried the [link]("http://www.ubuntuforums.org/showthread.php?t=326128") i mentioned earlier?.

---

### Post by Kingfield on 2007-01-11
yea i tried same S3TC error

---

### Post by Kingfield on 2007-01-11
> **RomeReactor said:**
> When you run rolauncher, after you type your password and the screen with the two mages appears, you'll see below "Options" (or "Opciones", if it's in spanish). Click there to set the game to run on your desired resolution, but set it on 16-bit color, eg. 1024x768x**16**. In the Regnum forums your card's status is "unknown", which means the game may or may not run on it. Have you tried the [link]("http://www.ubuntuforums.org/showthread.php?t=326128") i mentioned earlier?.

no, but glxgears works perfectly well

---

### Post by RomeReactor on 2007-01-11
Do you have the savage drivers? Try:

```
man savage
```

If the man page doesn't come up look for the drivers in Synaptic. I think you need to have universe and multiverse repositories enabled. Or you can install them from the terminal:

```
sudo apt-get install xserver-xorg-video-savage
```

Also check your xorg.con file to see if you're using those drivers:

```
sudo gedit /etc/X11/xorg.conf
```

Scroll down to:

Section "Device"

And see what driver you are using. It may be necessary to change it from "mesa" to "savage".
My integrated video card appears to be Savage also; though i've never used it (i have a geforce 6200), i have the drivers installed. Keep in mind that changing from mesa to savage drivers may break your xserver, in which case you'll be dumped to the terminal next time you login. If that happens, write:

```
sudo nano /etc/X11/xorg.conf
```

again scroll down to the "Device" section, change the driver back to mesa, press CTRL + O to save, CTRL + X to quit nano, and restart:

```
sudo reboot
```

You should have X running agian...

---

### Post by Kingfield on 2007-01-13
yes, i am using the savage drivers.

---

### Post by RomeReactor on 2007-01-13
Let's try this:

```
cat /var/log/Xorg.0.log | grep SAVAGE
```

Post the output and your Xorg.conf, please. Have you tried asking for help in the ubuntu irc channel?

---

### Post by Kingfield on 2007-01-15
wow... large outpput!! brace yourself!

```
cat /var/log/Xorg.0.log | grep SAVAGEkingfield@kingfield-desktop:~$ cat /var/log/Xorg.0.log | grep SAVAGE
(II) SAVAGE: driver (version 2.0.2) for S3 Savage chipsets: Savage4,
(**) SAVAGE(0): Depth 16, (--) framebuffer bpp 16
(==) SAVAGE(0): RGB weight 565
(==) SAVAGE(0): Default visual is TrueColor
(II) SAVAGE(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) SAVAGE(0): Using HW cursor
(==) SAVAGE(0): Using video BIOS to set modes
(II) SAVAGE(0): initializing int10
(II) SAVAGE(0): Primary V_BIOS segment is: 0xc000
(II) SAVAGE(0): VESA BIOS detected
(II) SAVAGE(0): VESA VBE Version 2.0
(II) SAVAGE(0): VESA VBE Total Mem: 8192 kB
(II) SAVAGE(0): VESA VBE OEM: S3 Incorporated. Savage4
(II) SAVAGE(0): VESA VBE OEM Software Rev: 1.1
(II) SAVAGE(0): VESA VBE OEM Vendor: Number Nine Visual Technology Corporation
(II) SAVAGE(0): VESA VBE OEM Product: SR9
(II) SAVAGE(0): VESA VBE OEM Product Rev: Rev C
(--) SAVAGE(0): Chip: id 8a22, "Savage4"
(--) SAVAGE(0): Engine: "Savage4"
(--) SAVAGE(0): AGP card detected
(==) SAVAGE(0): Using AGP DMA
(==) SAVAGE(0): Will try command and vertex DMA mode
(==) SAVAGE(0): Using AGP 1x mode
(==) SAVAGE(0): Using 16 MB AGP aperture
(II) SAVAGE(0): mapping MMIO @ 0xe0000000 with size 0x80000
(==) SAVAGE(0): Using gamma correction (1.0, 1.0, 1.0)
(--) SAVAGE(0): probed videoram:  8192k
(--) SAVAGE(0): No DDC signal
(II) SAVAGE(0): I2C bus "I2C bus" initialized.
(II) SAVAGE(0): I2C device "I2C bus:ddc2" registered at address 0xA0.
(II) SAVAGE(0): I2C device "I2C bus:ddc2" removed.
(II) SAVAGE(0): Manufacturer: STC  Model: 0  Serial#: 2
(II) SAVAGE(0): Year: 2001  Week: 34
(II) SAVAGE(0): EDID Version: 1.2
(II) SAVAGE(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) SAVAGE(0): Sync:  Separate
(II) SAVAGE(0): Max H-Image Size [cm]: horiz.: 30  vert.: 22
(II) SAVAGE(0): Gamma: 2.81
(II) SAVAGE(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) SAVAGE(0): redX: 0.604 redY: 0.344   greenX: 0.322 greenY: 0.545
(II) SAVAGE(0): blueX: 0.156 blueY: 0.117   whiteX: 0.312 whiteY: 0.329
(II) SAVAGE(0): Supported VESA Video Modes:
(II) SAVAGE(0): 720x400@70Hz
(II) SAVAGE(0): 640x480@60Hz
(II) SAVAGE(0): 640x480@67Hz
(II) SAVAGE(0): 640x480@72Hz
(II) SAVAGE(0): 640x480@75Hz
(II) SAVAGE(0): 800x600@56Hz
(II) SAVAGE(0): 800x600@60Hz
(II) SAVAGE(0): 800x600@72Hz
(II) SAVAGE(0): 800x600@75Hz
(II) SAVAGE(0): 832x624@75Hz
(II) SAVAGE(0): 1024x768@60Hz
(II) SAVAGE(0): 1024x768@70Hz
(II) SAVAGE(0): 1024x768@75Hz
(II) SAVAGE(0): Manufacturer's mask: 0
(II) SAVAGE(0): Monitor name: 15" LCD
(II) SAVAGE(0): Monitor name: Monitor
(II) SAVAGE(0): Ranges: V min: 56  V max: 75 Hz, H min: 31  H max: 60 kHz, PixClock max 80 MHz
(II) SAVAGE(0): Serial No: 2
(--) SAVAGE(0): Detected current MCLK value of 109.773 MHz
(--) SAVAGE(0): Found 14 modes at this depth:
(II) SAVAGE(0): 15 LCD: Using hsync range of 31.00-60.00 kHz
(II) SAVAGE(0): 15 LCD: Using vrefresh range of 56.00-75.00 Hz
(II) SAVAGE(0): Clock range:  10.00 to 250.00 MHz
(--) SAVAGE(0): No suitable BIOS mode found for 640x350 85Hz.
(II) SAVAGE(0): Not using default mode "640x350" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 320x175 85Hz.
(II) SAVAGE(0): Not using default mode "320x175" (no mode of this name)
(--) SAVAGE(0): Chose mode 11d at 70Hz.
(II) SAVAGE(0): Not using default mode "640x400" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 10e at 70Hz.
(II) SAVAGE(0): Not using default mode "320x200" (vrefresh out of range)
(--) SAVAGE(0): No suitable BIOS mode found for 720x400 85Hz.
(II) SAVAGE(0): Not using default mode "720x400" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 360x200 85Hz.
(II) SAVAGE(0): Not using default mode "360x200" (no mode of this name)
(--) SAVAGE(0): Chose mode 111 at 60Hz.
(--) SAVAGE(0): Chose mode 133 at 72Hz.
(--) SAVAGE(0): Chose mode 111 at 72Hz.
(--) SAVAGE(0): Chose mode 133 at 72Hz.
(--) SAVAGE(0): Chose mode 111 at 75Hz.
(--) SAVAGE(0): Chose mode 133 at 72Hz.
(--) SAVAGE(0): Chose mode 111 at 85Hz.
(II) SAVAGE(0): Not using default mode "640x480" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 133 at 72Hz.
(II) SAVAGE(0): Not using default mode "320x240" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 114 at 56Hz.
(--) SAVAGE(0): Chose mode 143 at 72Hz.
(--) SAVAGE(0): Chose mode 114 at 60Hz.
(--) SAVAGE(0): Chose mode 143 at 72Hz.
(--) SAVAGE(0): Chose mode 114 at 72Hz.
(--) SAVAGE(0): Chose mode 143 at 72Hz.
(--) SAVAGE(0): Chose mode 114 at 75Hz.
(--) SAVAGE(0): Chose mode 143 at 72Hz.
(--) SAVAGE(0): Chose mode 114 at 85Hz.
(II) SAVAGE(0): Not using default mode "800x600" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 143 at 72Hz.
(II) SAVAGE(0): Not using default mode "400x300" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 117 at 85Hz.
(II) SAVAGE(0): Not using default mode "1024x768" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 153 at 70Hz.
(II) SAVAGE(0): Not using default mode "512x384" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 117 at 60Hz.
(--) SAVAGE(0): Chose mode 153 at 70Hz.
(--) SAVAGE(0): Chose mode 117 at 70Hz.
(--) SAVAGE(0): Chose mode 153 at 70Hz.
(--) SAVAGE(0): Chose mode 117 at 75Hz.
(--) SAVAGE(0): Chose mode 153 at 70Hz.
(--) SAVAGE(0): Chose mode 117 at 85Hz.
(II) SAVAGE(0): Not using default mode "1024x768" (hsync out of range)
(--) SAVAGE(0): Chose mode 153 at 70Hz.
(II) SAVAGE(0): Not using default mode "512x384" (hsync out of range)
(--) SAVAGE(0): Chose mode 163 at 75Hz.
(II) SAVAGE(0): Not using default mode "1152x864" (hsync out of range)
(--) SAVAGE(0): No suitable BIOS mode found for 576x432 75Hz.
(II) SAVAGE(0): Not using default mode "576x432" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1280x960 60Hz.
(II) SAVAGE(0): Not using default mode "1280x960" (no mode of this name)
(--) SAVAGE(0): Chose mode 111 at 60Hz.
(--) SAVAGE(0): No suitable BIOS mode found for 1280x960 85Hz.
(II) SAVAGE(0): Not using default mode "1280x960" (no mode of this name)
(--) SAVAGE(0): Chose mode 111 at 85Hz.
(II) SAVAGE(0): Not using default mode "640x480" (hsync out of range)
(--) SAVAGE(0): Chose mode 11a at 60Hz.
(II) SAVAGE(0): Not using default mode "1280x1024" (hsync out of range)
(--) SAVAGE(0): No suitable BIOS mode found for 640x512 60Hz.
(II) SAVAGE(0): Not using default mode "640x512" (no mode of this name)
(--) SAVAGE(0): Chose mode 11a at 75Hz.
(II) SAVAGE(0): Not using default mode "1280x1024" (hsync out of range)
(--) SAVAGE(0): No suitable BIOS mode found for 640x512 75Hz.
(II) SAVAGE(0): Not using default mode "640x512" (no mode of this name)
(--) SAVAGE(0): Chose mode 11a at 85Hz.
(II) SAVAGE(0): Not using default mode "1280x1024" (hsync out of range)
(--) SAVAGE(0): No suitable BIOS mode found for 640x512 85Hz.
(II) SAVAGE(0): Not using default mode "640x512" (no mode of this name)
(--) SAVAGE(0): Chose mode 122 at 60Hz.
(II) SAVAGE(0): Not using default mode "1600x1200" (hsync out of range)
(--) SAVAGE(0): Chose mode 114 at 60Hz.
(II) SAVAGE(0): Not using default mode "800x600" (hsync out of range)
(--) SAVAGE(0): Chose mode 122 at 60Hz.
(II) SAVAGE(0): Not using default mode "1600x1200" (hsync out of range)
(--) SAVAGE(0): Chose mode 114 at 60Hz.
(II) SAVAGE(0): Not using default mode "800x600" (hsync out of range)
(--) SAVAGE(0): Chose mode 122 at 75Hz.
(II) SAVAGE(0): Not using default mode "1600x1200" (hsync out of range)
(--) SAVAGE(0): Chose mode 114 at 72Hz.
(II) SAVAGE(0): Not using default mode "800x600" (hsync out of range)
(--) SAVAGE(0): Chose mode 122 at 75Hz.
(II) SAVAGE(0): Not using default mode "1600x1200" (hsync out of range)
(--) SAVAGE(0): Chose mode 114 at 75Hz.
(II) SAVAGE(0): Not using default mode "800x600" (hsync out of range)
(--) SAVAGE(0): Chose mode 122 at 85Hz.
(II) SAVAGE(0): Not using default mode "1600x1200" (hsync out of range)
(--) SAVAGE(0): Chose mode 114 at 85Hz.
(II) SAVAGE(0): Not using default mode "800x600" (hsync out of range)
(--) SAVAGE(0): No suitable BIOS mode found for 1792x1344 60Hz.
(II) SAVAGE(0): Not using default mode "1792x1344" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 896x672 60Hz.
(II) SAVAGE(0): Not using default mode "896x672" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(--) SAVAGE(0): No suitable BIOS mode found for 896x672 75Hz.
(II) SAVAGE(0): Not using default mode "896x672" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1856x1392 60Hz.
(II) SAVAGE(0): Not using default mode "1856x1392" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 928x696 60Hz.
(II) SAVAGE(0): Not using default mode "928x696" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(--) SAVAGE(0): No suitable BIOS mode found for 928x696 75Hz.
(II) SAVAGE(0): Not using default mode "928x696" (no mode of this name)
(--) SAVAGE(0): Chose mode 138 at 60Hz.
(II) SAVAGE(0): Not using default mode "1920x1440" (hsync out of range)
(--) SAVAGE(0): No suitable BIOS mode found for 960x720 60Hz.
(II) SAVAGE(0): Not using default mode "960x720" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(--) SAVAGE(0): No suitable BIOS mode found for 960x720 75Hz.
(II) SAVAGE(0): Not using default mode "960x720" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 832x624 74Hz.
(II) SAVAGE(0): Not using default mode "832x624" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 416x312 74Hz.
(II) SAVAGE(0): Not using default mode "416x312" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1280x768 60Hz.
(II) SAVAGE(0): Not using default mode "1280x768" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 640x384 60Hz.
(II) SAVAGE(0): Not using default mode "640x384" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1280x800 59Hz.
(II) SAVAGE(0): Not using default mode "1280x800" (no mode of this name)
(--) SAVAGE(0): Chose mode 11d at 70Hz.
(--) SAVAGE(0): No suitable BIOS mode found for 1152x768 54Hz.
(II) SAVAGE(0): Not using default mode "1152x768" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 576x384 54Hz.
(II) SAVAGE(0): Not using default mode "576x384" (no mode of this name)
(--) SAVAGE(0): Chose mode 163 at 85Hz.
(II) SAVAGE(0): Not using default mode "1152x864" (hsync out of range)
(--) SAVAGE(0): No suitable BIOS mode found for 576x432 85Hz.
(II) SAVAGE(0): Not using default mode "576x432" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1400x1050 59Hz.
(II) SAVAGE(0): Not using default mode "1400x1050" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 700x525 59Hz.
(II) SAVAGE(0): Not using default mode "700x525" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1400x1050 70Hz.
(II) SAVAGE(0): Not using default mode "1400x1050" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 700x525 70Hz.
(II) SAVAGE(0): Not using default mode "700x525" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1400x1050 74Hz.
(II) SAVAGE(0): Not using default mode "1400x1050" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 700x525 74Hz.
(II) SAVAGE(0): Not using default mode "700x525" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1400x1050 85Hz.
(II) SAVAGE(0): Not using default mode "1400x1050" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 700x525 85Hz.
(II) SAVAGE(0): Not using default mode "700x525" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1440x900 60Hz.
(II) SAVAGE(0): Not using default mode "1440x900" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 720x450 60Hz.
(II) SAVAGE(0): Not using default mode "720x450" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1600x1024 59Hz.
(II) SAVAGE(0): Not using default mode "1600x1024" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 800x512 60Hz.
(II) SAVAGE(0): Not using default mode "800x512" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1680x1050 60Hz.
(II) SAVAGE(0): Not using default mode "1680x1050" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 840x525 60Hz.
(II) SAVAGE(0): Not using default mode "840x525" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1680x1050 59Hz.
(II) SAVAGE(0): Not using default mode "1680x1050" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 840x525 60Hz.
(II) SAVAGE(0): Not using default mode "840x525" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1680x1050 84Hz.
(II) SAVAGE(0): Not using default mode "1680x1050" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 840x525 85Hz.
(II) SAVAGE(0): Not using default mode "840x525" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1920x1200 60Hz.
(II) SAVAGE(0): Not using default mode "1920x1200" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 960x600 60Hz.
(II) SAVAGE(0): Not using default mode "960x600" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 1920x1200 72Hz.
(II) SAVAGE(0): Not using default mode "1920x1200" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 960x600 72Hz.
(II) SAVAGE(0): Not using default mode "960x600" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(--) SAVAGE(0): No suitable BIOS mode found for 960x720 85Hz.
(II) SAVAGE(0): Not using default mode "960x720" (no mode of this name)
(II) SAVAGE(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(--) SAVAGE(0): Chose mode 117 at 60Hz.
(II) SAVAGE(0): Not using default mode "1024x768" (hsync out of range)
(II) SAVAGE(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(--) SAVAGE(0): Chose mode 117 at 75Hz.
(II) SAVAGE(0): Not using default mode "1024x768" (hsync out of range)
(II) SAVAGE(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(--) SAVAGE(0): Chose mode 117 at 85Hz.
(II) SAVAGE(0): Not using default mode "1024x768" (hsync out of range)
(--) SAVAGE(0): Chose mode 117 at 75Hz.
(--) SAVAGE(0): Chose mode 114 at 75Hz.
(--) SAVAGE(0): Chose mode 111 at 75Hz.
(--) SAVAGE(0): Chose mode 117 at 70Hz.
(--) SAVAGE(0): Chose mode 117 at 60Hz.
(--) SAVAGE(0): Chose mode 114 at 72Hz.
(--) SAVAGE(0): Chose mode 114 at 60Hz.
(--) SAVAGE(0): Chose mode 114 at 56Hz.
(--) SAVAGE(0): Chose mode 111 at 72Hz.
(--) SAVAGE(0): Chose mode 111 at 60Hz.
(--) SAVAGE(0): Chose mode 111 at 60Hz.
(--) SAVAGE(0): Chose mode 11d at 70Hz.
(--) SAVAGE(0): Chose mode 153 at 70Hz.
(--) SAVAGE(0): Chose mode 153 at 70Hz.
(--) SAVAGE(0): Chose mode 153 at 70Hz.
(--) SAVAGE(0): Chose mode 143 at 72Hz.
(--) SAVAGE(0): Chose mode 143 at 72Hz.
(--) SAVAGE(0): Chose mode 143 at 72Hz.
(--) SAVAGE(0): Chose mode 143 at 72Hz.
(--) SAVAGE(0): Chose mode 133 at 72Hz.
(--) SAVAGE(0): Chose mode 133 at 72Hz.
(--) SAVAGE(0): Chose mode 133 at 72Hz.
(--) SAVAGE(0): Virtual size is 1024x768 (pitch 1024)
(**) SAVAGE(0): *Default mode "1024x768": 78.8 MHz, 60.1 kHz, 75.1 Hz
(II) SAVAGE(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(**) SAVAGE(0): *Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) SAVAGE(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(**) SAVAGE(0): *Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) SAVAGE(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(**) SAVAGE(0):  Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) SAVAGE(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(**) SAVAGE(0):  Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) SAVAGE(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(**) SAVAGE(0):  Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) SAVAGE(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(**) SAVAGE(0):  Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) SAVAGE(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) SAVAGE(0):  Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) SAVAGE(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(**) SAVAGE(0):  Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) SAVAGE(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(**) SAVAGE(0):  Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) SAVAGE(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(**) SAVAGE(0):  Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (D)
(II) SAVAGE(0): Modeline "640x480"   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync
(**) SAVAGE(0):  Default mode "640x400": 41.7 MHz, 49.7 kHz, 60.0 Hz (D)
(II) SAVAGE(0): Modeline "640x400"   41.73  640 672 740 840  400 400 402 414 doublescan
(**) SAVAGE(0):  Default mode "512x384": 39.4 MHz, 60.1 kHz, 75.1 Hz (D)
(II) SAVAGE(0): Modeline "512x384"   39.40  512 520 568 656  384 384 386 400 doublescan +hsync +vsync
(**) SAVAGE(0):  Default mode "512x384": 37.5 MHz, 56.5 kHz, 70.1 Hz (D)
(II) SAVAGE(0): Modeline "512x384"   37.50  512 524 592 664  384 385 388 403 doublescan -hsync -vsync
(**) SAVAGE(0):  Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(II) SAVAGE(0): Modeline "512x384"   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync
(**) SAVAGE(0):  Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(II) SAVAGE(0): Modeline "400x300"   24.75  400 408 448 528  300 300 302 312 doublescan +hsync +vsync
(**) SAVAGE(0):  Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(II) SAVAGE(0): Modeline "400x300"   25.00  400 428 488 520  300 318 321 333 doublescan +hsync +vsync
(**) SAVAGE(0):  Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) SAVAGE(0): Modeline "400x300"   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync
(**) SAVAGE(0):  Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) SAVAGE(0): Modeline "400x300"   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync
(**) SAVAGE(0):  Default mode "320x240": 15.8 MHz, 37.5 kHz, 75.0 Hz (D)
(II) SAVAGE(0): Modeline "320x240"   15.75  320 328 360 420  240 240 242 250 doublescan -hsync -vsync
(**) SAVAGE(0):  Default mode "320x240": 15.8 MHz, 37.9 kHz, 72.8 Hz (D)
(II) SAVAGE(0): Modeline "320x240"   15.75  320 332 352 416  240 244 245 260 doublescan -hsync -vsync
(**) SAVAGE(0):  Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) SAVAGE(0): Modeline "320x240"   12.60  320 328 376 400  240 245 246 262 doublescan -hsync -vsync
(--) SAVAGE(0): Display dimensions: (300, 220) mm
(--) SAVAGE(0): DPI set to (86, 88)
(II) SAVAGE(0): initializing int10
(II) SAVAGE(0): Primary V_BIOS segment is: 0xc000
(II) SAVAGE(0): VESA BIOS detected
(II) SAVAGE(0): VESA VBE Version 2.0
(II) SAVAGE(0): VESA VBE Total Mem: 8192 kB
(II) SAVAGE(0): VESA VBE OEM: S3 Incorporated. Savage4
(II) SAVAGE(0): VESA VBE OEM Software Rev: 1.1
(II) SAVAGE(0): VESA VBE OEM Vendor: Number Nine Visual Technology Corporation
(II) SAVAGE(0): VESA VBE OEM Product: SR9
(II) SAVAGE(0): VESA VBE OEM Product Rev: Rev C
(--) SAVAGE(0): mapping framebuffer @ 0xd8000000 with size 0x800000
(II) SAVAGE(0): map aperture:0xb2063000
(II) SAVAGE(0): 4740 kB of Videoram needed for 3D; 8192 kB of Videoram available(II) SAVAGE(0): Sufficient Videoram available for 3D
(II) SAVAGE(0): [drm] bpp: 16 depth: 16
(II) SAVAGE(0): [drm] Sarea 2200+284: 2484
(II) SAVAGE(0): [drm] DRM interface version 1.2
(II) SAVAGE(0): [drm] created "savage" driver at busid "pci:0000:01:00.0"
(II) SAVAGE(0): [drm] added 8192 byte SAREA at 0xd0c56000
(II) SAVAGE(0): [drm] mapped SAREA 0xd0c56000 to 0xb2051000
(II) SAVAGE(0): [drm] framebuffer handle = 0xd8000000
(II) SAVAGE(0): [drm] added 1 reserved context for kernel
(II) SAVAGE(0): [agp] Mode 0x1f000201 [AGP 0x1039/0x0646; Card 0x5333/0x8a22]
(II) SAVAGE(0): [agp] 16384 kB allocated with handle 0x00000001
(II) SAVAGE(0): [agp] command DMA handle = 0xd0000000
(II) SAVAGE(0): [agp] agpTextures handle = 0xd0100000
(II) SAVAGE(0): [drm] aperture handle = 0xda000000
(II) SAVAGE(0): [drm] Enabling ShadowStatus for DRI.
(II) SAVAGE(0): [drm] Status handle = 0x0be76000
(II) SAVAGE(0): [drm] Status page mapped at 0xb2050000
(II) SAVAGE(0): [dri] visual configs initialized
(**) SAVAGE(0): DRI is enabled
(--) SAVAGE(0): Chose mode 117 at 75Hz.
(II) SAVAGE(0): virtualX:1024,virtualY:768
(II) SAVAGE(0): bpp:16,tiledwidthBytes:2048,tiledBufferSize:1572864
(II) SAVAGE(0): bpp:16,widthBytes:2048,BufferSize:1572864
(II) SAVAGE(0): videoRambytes:0x00800000
(II) SAVAGE(0): textureSize:0x0015f000
(II) SAVAGE(0): textureSize:0x0015f000
(II) SAVAGE(0): textureOffset:0x00680000
(II) SAVAGE(0): depthOffset:0x00500000,depthPitch:2048
(II) SAVAGE(0): backOffset:0x00380000,backPitch:2048
(II) SAVAGE(0): Memory manager initialized to (0,0) (1024,1791)
(II) SAVAGE(0): Largest offscreen area available: 1024 x 1023
(II) SAVAGE(0): Reserved back buffer at offset 0x380000
(II) SAVAGE(0): Reserved depth buffer at offset 0x500000
(II) SAVAGE(0): Reserved 1404 kb for textures at offset 0x680000
(II) SAVAGE(0): Using XFree86 Acceleration Architecture (XAA)
(==) SAVAGE(0): Backing store disabled
(**) SAVAGE(0): DPMS enabled
(II) SAVAGE(0): X context handle = 0x1
(II) SAVAGE(0): [DRI] installation complete
(II) SAVAGE(0): [junkers]pSAVAGEDRIServer:
(II) SAVAGE(0): [junkers]       reserved_map_agpstart:0x00000000
(II) SAVAGE(0): [junkers]       reserved_map_idx:0x00000000
(II) SAVAGE(0): [junkers]       sarea_priv_offset:0x00000000
(II) SAVAGE(0): [junkers]       chipset:0x00000000
(II) SAVAGE(0): [junkers]       sgram:0x00000000
(II) SAVAGE(0): [junkers]       frontbufferSize:0x00180000
(II) SAVAGE(0): [junkers]       frontOffset:0x00000000
(II) SAVAGE(0): [junkers]       frontPitch:0x00000800
(II) SAVAGE(0): [junkers]       backbufferSize:0x00180000
(II) SAVAGE(0): [junkers]       backOffset:0x00380000
(II) SAVAGE(0): [junkers]       backPitch:0x00000800
(II) SAVAGE(0): [junkers]       depthbufferSize:0x00180000
(II) SAVAGE(0): [junkers]       depthOffset:0x00500000
(II) SAVAGE(0): [junkers]       depthPitch:0x00000800
(II) SAVAGE(0): [junkers]       textureOffset:0x00680000
(II) SAVAGE(0): [junkers]       textureSize:0x0015f000
(II) SAVAGE(0): [junkers]       textureSize:0x0015f000
(II) SAVAGE(0): [junkers]       logTextureGranularity:0x00000000
(II) SAVAGE(0): [junkers]       agp:handle:0x00000001
(II) SAVAGE(0): [junkers]       agp:offset:0x01000000
(II) SAVAGE(0): [junkers]       agp:size:0x01000000
(II) SAVAGE(0): [junkers]       agp:map:0x00000000
(II) SAVAGE(0): [junkers]       registers:handle:0xe0000000
(II) SAVAGE(0): [junkers]       registers:offset:0x00000000
(II) SAVAGE(0): [junkers]       registers:size:0x00080000
(II) SAVAGE(0): [junkers]       registers:map:0x00000000
(II) SAVAGE(0): [junkers]       status:handle:0x0be76000
(II) SAVAGE(0): [junkers]       status:offset:0x00000000
(II) SAVAGE(0): [junkers]       status:size:0x00001000
(II) SAVAGE(0): [junkers]       status:map:0xb2050000
(II) SAVAGE(0): [junkers]       agpTextures:handle:0xd0100000
(II) SAVAGE(0): [junkers]       agpTextures:offset:0x00100000
(II) SAVAGE(0): [junkers]       agpTextures:size:0x00f00000
(II) SAVAGE(0): [junkers]       apgTextures:map:0x00000000
(II) SAVAGE(0): [junkers]       logAgpTextureGranularity:0x00000000
(II) SAVAGE(0): [junkers]       cmdDma:handle:0xd0000000
(II) SAVAGE(0): [junkers]       cmdDma:offset:0x00000000
(II) SAVAGE(0): [junkers]       cmdDma:size:0x00100000
(II) SAVAGE(0): [junkers]       cmdDma:map:0x00000000
(II) SAVAGE(0): [junkers]pSAVAGEDRI:
(II) SAVAGE(0): [junkers]       chipset:0x00000003
(II) SAVAGE(0): [junkers]       width:0x00000400
(II) SAVAGE(0): [junkers]       height:0x00000300
(II) SAVAGE(0): [junkers]       mem:0x00800000
(II) SAVAGE(0): [junkers]       cpp:2
(II) SAVAGE(0): [junkers]       zpp:2
(II) SAVAGE(0): [junkers]       agpMode:1
(II) SAVAGE(0): [junkers]       bufferSize:65536
(II) SAVAGE(0): [junkers]       frontbufferSize:0x00180000
(II) SAVAGE(0): [junkers]       frontOffset:0x00000000
(II) SAVAGE(0): [junkers]       backbufferSize:0x00180000
(II) SAVAGE(0): [junkers]       backOffset:0x00380000
(II) SAVAGE(0): [junkers]       depthbufferSize:0x00180000
(II) SAVAGE(0): [junkers]       depthOffset:0x00500000
(II) SAVAGE(0): [junkers]       textureOffset:0x00680000
(II) SAVAGE(0): [junkers]       textureSize:0x00140000
(II) SAVAGE(0): [junkers]       logTextureGranularity:0x00000011
(II) SAVAGE(0): [junkers]       agpTextureHandle:0xd0100000
(II) SAVAGE(0): [junkers]       agpTextureSize:0x00f00000
(II) SAVAGE(0): [junkers]       logAgpTextureGranularity:0x00000014
(II) SAVAGE(0): [junkers]       apertureHandle:0xda000000
(II) SAVAGE(0): [junkers]       apertureSize:0x05000000
(II) SAVAGE(0): [junkers]       aperturePitch:0x00001000
(II) SAVAGE(0): [junkers]       statusHandle:0x0be76000
(II) SAVAGE(0): [junkers]       statusSize:0x00001000
(II) SAVAGE(0): [junkers]       sarea_priv_offset:0x00000898
(II) SAVAGE(0): Direct rendering enabled
(II) SAVAGE(0): v4l[/dev/video0]: using hw video scaling [YUY2].

```

---

### Post by RomeReactor on 2007-01-15
Please post your Xorg.conf, too. By the way, did you try to add

```
Option "BusType" "PCI"
```

to the "Device" section in your Xorg.conf, then reboot, and see if the game worked?

---

### Post by Kingfield on 2007-01-15
ok wait ill try that

---

### Post by Kingfield on 2007-02-17
Sorry i was away for long, it didnt work.

---

### Post by Kingfield on 2007-02-17
Not only that it didnt work, whenever i open an OpenGL using program, the computer freezes up - so i have removed it for now. Any ideas?

---

### Post by Kingfield on 2007-02-18
bumpage

---

