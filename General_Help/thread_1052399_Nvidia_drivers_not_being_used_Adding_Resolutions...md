---
title: "Nvidia drivers not being used? Adding Resolutions..."
date: 2009-01-27
forum: General Help
---

### Post by PoopyTheJ on 2009-01-27
The Nvidia X Configuration utility says I don;t appear to be using the nvidia driver, though xorg.conf shows nvidia as the driver being used and I get an Nvidia splash screen when I boot. Also I'm now limited to 800x600 which I wasn't limited to using Vesa. It's an old computer but the monitor will support more than 800x600. How do I either get x to recognize my monitor, which it did using Vesa or enable more resolutions manually?

---

### Post by taurus on 2009-01-27
Go into System -> Preferences -> Screen Resolution and see if you can increase the resolution for your monitor.

---

### Post by PoopyTheJ on 2009-01-27
No can do, it will only allow me to run at 800x600 at 60hz, which well hurts.

---

### Post by taurus on 2009-01-27
What graphic card do you have?

```
lspci | grep VGA
```
See if your system is really using nvidia driver.

```
lsmod
```

---

### Post by PoopyTheJ on 2009-01-27
```
01:00.0 VGA compatible controller: nVidia Corporation NV6 [Vanta/Vanta LT] (rev 15)

```

```
Module                  Size  Used by
ipv6                  267908  8 
binfmt_misc            12808  1 
af_packet              23812  2 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61028  4 rfcomm,l2cap
ppdev                  10372  0 
apm                    22616  2 
speedstep_lib           6532  0 
cpufreq_userspace       5284  0 
cpufreq_conservative     8712  0 
cpufreq_ondemand        9740  0 
cpufreq_stats           7104  0 
freq_table              5536  2 cpufreq_ondemand,cpufreq_stats
cpufreq_powersave       2688  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
lp                     12324  0 
snd_ens1371            27168  3 
gameport               16008  1 snd_ens1371
snd_ac97_codec        101028  1 snd_ens1371
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  3 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
evdev                  13056  1 
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
snd_rawmidi            25760  2 snd_ens1371,snd_seq_midi
nvidia               3922508  8 
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
serio_raw               7940  0 
psmouse                40336  0 
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  17 snd_ens1371,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcspkr                  4224  0 
soundcore               8800  1 snd
snd_page_alloc         11400  1 snd_pcm
i2c_piix4               9612  0 
i2c_core               24832  1 i2c_piix4
intel_agp              25492  1 
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
agpgart                34760  2 nvidia,intel_agp
ext3                  136840  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
usbhid                 32128  0 
hid                    38784  1 usbhid
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  3 
floppy                 59588  0 
ata_piix               19588  2 
ata_generic             8324  0 
pata_acpi               8320  0 
uhci_hcd               27024  0 
libata                159600  3 ata_piix,ata_generic,pata_acpi
8139too                27520  0 
mii                     6400  1 8139too
usbcore               146412  3 usbhid,uhci_hcd
scsi_mod              151436  4 sg,sr_mod,sd_mod,libata
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3 

```

---

### Post by taurus on 2009-01-27
Have you looked at System -> Administration ->  Nvidia Settings?

---

### Post by PoopyTheJ on 2009-01-27
Nvidia X Server Settings applet gives me this error when starting

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

Also I can click the check boxes next to Enable Tooltips, diplay status bar etc but that's it.

---

### Post by PoopyTheJ on 2009-01-27
also sudo nvidia-xconfig gives me this...

```
sudo: nvidia-xconfig: command not found
```

---

### Post by PoopyTheJ on 2009-01-27
if I try to install nvidia-xconfig through synaptic it wants to uninstall the nvidia-legacy-envy drivers, which was the only way I got what I have installed installed, if there's another or a better way to install the nvidia legacy drivers I'm willing to try it, but just trying to install the restricted drivers through the normal restricted hardware drivers prompt got me booting to a low resolution desktop

---

### Post by PoopyTheJ on 2009-01-27
So I reinstalled the nvidia drivers from the package available on Nvidia's site, installed correctly and rebooted changing xorg.conf to nvidia. Once again stuck at 800x600 and the nvidia xserver settings module again says I'm not using the nvidia driver. Ran nvidi-xconfig and got...

```
Using X configuration file: "/etc/X11/xorg.conf".

WARNING: The CorePointer device was not specified explicitly in the layout;
         using the first CorePointer in the config input list.


WARNING: Unable to determine CoreKeyboard; will rely on X server's built-in
         default configuration.

Segmentation fault

```

---

### Post by PoopyTheJ on 2009-01-27
Ok the segmentation fault was because the Modules "glx" wasn't in Xorg.conf, of course that's what nvidia-xconfig is supposed to do but whatever, after adding that xconfig ran as expected, rebooted and still nvidia x server settings says I'm not using the nvidia driver, though clearly I am. Below is my xorg.conf file. lsmod and lspci | grep are the same as above...

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildd@palmer)  Tue Jan 22 12:05:14 UTC 2008

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "NvAGP" "2"
    Option         "AllowDDCCI" "Enable"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
```

---

### Post by PoopyTheJ on 2009-01-27
glxinfo shows...

```
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x23 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x24 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x25 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x26 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x27 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x28 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x29 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x2a 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x2b 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x2c 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x2d 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x2e 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x2f 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x30 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x81 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Segmentation fault
```

---

### Post by PoopyTheJ on 2009-01-27
okay added composite "disable" to xorg.conf and now glxinfo shows...

```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.3
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control
client glx vendor string: NVIDIA Corporation
client glx version string: 1.3
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_NV_float_buffer
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: RIVA TNT2/AGP/SSE
OpenGL version string: 1.5.3 NVIDIA 71.86.06
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_point_parameters, 
    GL_ARB_texture_env_add, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, GL_ARB_window_pos, 
    GL_EXT_texture_env_add, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_compiled_vertex_array, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, 
    GL_EXT_pixel_buffer_object, GL_EXT_point_parameters, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_vertex_array, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_KTX_buffer_region, GL_NV_blend_square, GL_NV_fog_distance, 
    GL_NV_light_max_exponent, GL_NV_packed_depth_stencil, 
    GL_NV_texgen_reflection, GL_NV_texture_env_combine4, GL_SGIS_multitexture, 
    GL_SUN_slice_accum

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x2a 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x2b 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x2e 24 dc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x2f 24 dc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
```


Of course still the damn Nvidia X Server settings module still says I'm not using the nvidia driver and I still can't choose any other resolution than 800x600.

---

### Post by PoopyTheJ on 2009-01-30
I'm bumping this as I still haven't found a problem and hopefully new eyes will see it ;)

---

### Post by Yumi on 2009-01-30
This is not a help message, just to say that I have exactly the same problem since the update a few days ago. After the update it asked me about a replace ........ image /keep existing (something like this)  to which I replied yes. Since I am trying everything just like you.

Michael

---

### Post by sir_cheats_a_lot on 2009-01-30
you need to blacklist the nvidia driver that comes with ubuntu in order to use the proprietary one.. otherwise ubuntu will ignore the good driver completely, resulting in what you are experiencing right now.  had to do it myself when i upgraded to hardy.

---

### Post by Yumi on 2009-01-30
How would I "blacklist" the ubuntu nvidia driver?

At the moment, very weired, Ubuntu is upgrading to 8.10 which I had done manually back when it came out! Just enabled recommended updates in synaptics. Have to wait until this is done.

Michael

---

### Post by sir_cheats_a_lot on 2009-01-30
I'm a bit embarrassed to admit ... as i just did this a couple months ago.. but i seem to have forgotten.  it was mentioned in one of the how-tos i think.. either that or it was a previous post here in the forum.

---

### Post by sir_cheats_a_lot on 2009-01-30
ah-ha! there we go.  
the howto is here:
[http://ubuntuforums.org/showthread.php?t=1036788](http://ubuntuforums.org/showthread.php?t=1036788)

```
sudo gedit /etc/default/linux-restricted-modules-common
```
and add the modules nv nvidia_new to the list of disabled modules.

should look something like:
```
# This file is sourced from the linux-restricted-modules-common init
# script and is used to disable the link-on-boot feature, one module
# at a time.  This can be useful if you want to use hand-compiled
# versions of one or more modules, but keep linux-restricted-modules
# installed on your system, or just to disable modules you don't use
# and speed up your boot process by a second or two.
#
# Use a space-separated list of modules you wish to not have linked
# on boot.  The following example shows a (condensed) list of all
# modules shipped in the linux-restricted-modules packages:
#
# DISABLED_MODULES="ath_hal fc fglrx ltm nv"
#
# Note that disabling "fc" disables all fcdsl drivers, "ltm" disables
# ltmodem and ltserial, and "nv" disables the three nvidia drivers.
# You can also name each module individually, if you prefer a subset.

DISABLED_MODULES="nv nvidia_new"
```
:popcorn:

---

### Post by Yumi on 2009-01-31
Well - its working now with Proprietary drivers version 173!

But the way is strange. I installed Intrepid month ago - I insist! This afternoon I enabled in Synaptics Packet Manager - Settings - Repositoris - Updates - Proposed updates.

After this Ubuntu insisted to upgrade to 8.10 which I ok'd. Downloaded 1200 or more files, installed for hours.

Now in System - Administration - Hardware drivers  I have 3 Nvidia drivers for choice, version 177 being recommended. I enabled it and everything, including Google Earth is working.

Not what I call a solution, but it is working.

Michael

---

### Post by PoopyTheJ on 2009-01-31
In 8.04 after installing the drivers from nvidia and being stuck in 800x600 I enabled the restricted drivers without doing anything the the currently installed nvidia drivers. Rebooted now all my resolutions are available, glxinfo complains of conflicting drivers though. Not recommended but for now I have my resolutions

---

### Post by PoopyTheJ on 2009-02-03
ok uninstalled both nvidia and the ubuntu nvidia restricted drivers, then reinstalled the ubuntu restricted drivers and now they work. No idea just glad it got resolved.

---

