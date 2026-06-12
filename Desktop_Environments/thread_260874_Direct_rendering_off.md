---
title: "Direct rendering: off"
date: 2006-09-19
forum: Desktop Environments
---

### Post by Zaggy on 2006-09-19
Hi, I'm using a GF6600GT videocard and Asus A8V Deluxe motherboard.

I've installed the nvidia drivers with succes with the [envy]("http://http://www.albertomilone.eu/europeo/nvidia_scripts1.html") package: 

And I get a nice Nvidia logo and I got XGL + Compiz working, superb!

BUT, I wanted to play some WC3, after I started X without XGL/compiz,
I tried to start WC3 with 'wine war3.exe', warcraft 3 loads and gives me the nice menu, but it's all terribly slow..
Okay, I start W3 with wine war3.exe -opengl', wine complains 'no opengl found'

I'm confused, so I run 'lspci | grep agp' and 'lspci | grep AGP' , both turn up nothing.

I run 'glxinfo | grep direct' and I get 'direct rendering: No'

I'm a bit clueless now, anyone has an idea?

Do I have to recompile the kernel with alternate AGP support?

Here is the output of glxinfo, lspci ,'cat /etc/X11/xorg.conf' and sbin/lsmod

> zaggynl@AMD3200L:~$ lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
0000:00:00.1 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
0000:00:00.2 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
0000:00:00.3 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
0000:00:00.4 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
0000:00:00.7 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
0000:00:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
0000:00:0a.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
0000:00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
0000:00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600/GeForce 6600 GT] (rev a2)
zaggynl@AMD3200L:~$


> zaggynl@AMD3200L:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method,
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe,
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info,
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync,
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer,
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float
GLX version: 1.2
GLX extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_SGIX_fbconfig, GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 6600 GT/AGP/SSE2/3DNOW!
OpenGL version string: 1.2 (2.0.2 NVIDIA 87.74)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_imaging, GL_ARB_multitexture,
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shadow,
    GL_ARB_texture_border_clamp, GL_ARB_texture_cube_map,
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine,
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat,
    GL_ARB_window_pos, GL_ARB_texture_non_power_of_two, GL_ARB_vertex_program,
    GL_ARB_fragment_program, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color,
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract,
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays,
    GL_EXT_packed_pixels, GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap,
    GL_EXT_texture3D, GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, GL_EXT_texture_lod,
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_vertex_array,
    GL_ATI_texture_mirror_once, GL_HP_occlusion_test,
    GL_IBM_texture_mirrored_repeat, GL_NV_blend_square,
    GL_NV_texgen_reflection, GL_NV_texture_rectangle,
    GL_NV_texture_env_combine4, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod,
    GL_SGIX_depth_texture, GL_SGIX_shadow

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon
zaggynl@AMD3200L:~$


> zaggynl@AMD3200L:~$ cat /etc/X11/xorg.conf
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Tue Aug  1 21:11:12 PDT 2006

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
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
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

        # path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "Buttons" "7"
    Option         "ButtonMapping" "1 2 3 6 7"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "false"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "17 Inch Dell"
    HorizSync       30.0 - 65.0
    VertRefresh     50.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
    Driver         "nvidia"
    Option         "RenderAccel"                "true"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
    Monitor        "17 Inch Dell"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

zaggynl@AMD3200L:~$



> zaggynl@AMD3200L:~$ /sbin/lsmod
Module                  Size  Used by
nvidia               4547540  20
nls_utf8                2176  1
ntfs                  103536  1
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              50020  4 rfcomm,l2cap
ipt_limit               2432  8
iptable_mangle          2944  0
ipt_LOG                 6912  8
ipt_MASQUERADE          3456  0
ip_nat                 19628  1 ipt_MASQUERADE
ipt_TOS                 2560  0
ipt_REJECT              5632  1
ip_conntrack_irc        6768  0
ip_conntrack_ftp        7792  0
ipt_state               2048  6
ip_conntrack           51500  5 ipt_MASQUERADE,ip_nat,ip_conntrack_irc,ip_conntrack_ftp,ipt_state
nfnetlink               6552  2 ip_nat,ip_conntrack
iptable_filter          3072  1
ip_tables              22400  8 ipt_limit,iptable_mangle,ipt_LOG,ipt_MASQUERADE,ipt_TOS,ipt_REJECT,ipt_state,iptable_filter
ppdev                   9220  0
cpufreq_userspace       4696  0
cpufreq_stats           5636  0
freq_table              4740  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
video                  16260  0
tc1100_wmi              6916  0
sony_acpi               5644  0
pcc_acpi               12416  0
hotkey                 11556  0
dev_acpi               11140  0
container               4608  0
button                  6672  0
acpi_sbs               19980  0
battery                 9988  1 acpi_sbs
ac                      5252  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
af_packet              22920  0
ipv6                  265728  8
dm_mod                 58936  1
md_mod                 72532  0
lm90                   13092  0
eeprom                  7056  0
w83627hf               26384  0
hwmon_vid               2816  1 w83627hf
i2c_isa                 4992  1 w83627hf
sr_mod                 16932  0
sbp2                   24196  0
lp                     11844  0
snd_seq_dummy           3844  0
snd_seq_oss            33536  0
snd_seq_midi            9376  0
snd_seq_midi_event      7552  2 snd_seq_oss,snd_seq_midi
tsdev                   8000  0
snd_seq                51984  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
pcspkr                  2180  0
parport_pc             35780  1
parport                36296  3 ppdev,lp,parport_pc
psmouse                36100  0
serio_raw               7300  0
snd_via82xx            28824  2
gameport               15496  1 snd_via82xx
snd_ac97_codec         93216  1 snd_via82xx
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
rtc                    13492  0
snd_pcm                89864  4 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  2 snd_seq,snd_pcm
snd_page_alloc         10632  2 snd_via82xx,snd_pcm
snd_mpu401_uart         7808  1 snd_via82xx
usb_storage            74304  1
snd_rawmidi            25504  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          8716  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd                    55268  14 snd_seq_oss,snd_seq,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore              10208  1 snd
i2c_viapro              8980  0
i2c_core               21904  7 nvidia,i2c_acpi_ec,lm90,eeprom,w83627hf,i2c_isa,i2c_viapro
skge                   38672  0
amd64_agp              12356  1
agpgart                34888  2 nvidia,amd64_agp
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
sg                     37920  0
evdev                   9856  1
ext3                  135816  1
jbd                    58772  1 ext3
ide_generic             1536  0
ehci_hcd               34184  0
uhci_hcd               33808  0
usbcore               130820  4 usb_storage,ehci_hcd,uhci_hcd
ohci1394               35124  0
ieee1394              299832  2 sbp2,ohci1394
ide_cd                 33028  0
cdrom                  38560  2 sr_mod,ide_cd
ide_disk               17664  3
via82cxxx               9988  0 [permanent]
generic                 5124  0
sd_mod                 19984  3
sata_via               10116  3
libata                 78992  1 sata_via
scsi_mod              139496  6 sr_mod,sbp2,usb_storage,sg,sd_mod,libata
thermal                13576  0
processor              23360  1 thermal
fan                     4868  0
capability              5000  0
commoncap               7296  1 capability
vga16fb                13704  1
vgastate               10368  1 vga16fb
fbcon                  42784  72
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit
zaggynl@AMD3200L:~$


---

### Post by DoorGunner on 2006-09-19
Hi Zaggy

I found a number of articles that speak about the same issues as you and I have with nvidia cards, direct rendering and XGL. [http://en.opensuse.org/Xgl](http://en.opensuse.org/Xgl) is one such article. 

I am curious what does glxgears give you. Mine is about 8000 fps with a geforce 6600gt card. It is somewhat degraded (aprox 1-2000fps) compared to normal Xorg numbers. WHen i loaded XGL i expected some slow downs as others have stated. However, i find them minimal. How do you find it so far?

I have no lag issues with xgl..... so i am wondering if xgl is direct rendered but just not reporting it to glxinfo?

---

### Post by Zaggy on 2006-09-19
Problem solved, I was still running XGL even if I left compiz off.
[you can't have direct rendering with XGL/Compiz]("http://www.ubuntuforums.org/showpost.php?p=1519121&postcount=147")
What I did to simply turn XGL off:

(I used method B from this [https://help.ubuntu.com/community/CompositeManager/Xgl]("https://help.ubuntu.com/community/CompositeManager/Xgl")

gksudo gedit /etc/gdm/gdm.conf-custom

and comment every line I added.

[servers]
#0=Xgl

#[server-Xgl] 
#name=Xgl server 
#command=/usr/bin/Xgl -fullscreen -br -accel xv:fbo -accel glx:pbuffer
#flexible=true

---

### Post by Zaggy on 2006-09-19
> **DoorGunner said:**
> Hi Zaggy

I found a number of articles that speak about the same issues as you and I have with nvidia cards, direct rendering and XGL. [http://en.opensuse.org/Xgl](http://en.opensuse.org/Xgl) is one such article. 

I am curious what does glxgears give you. Mine is about 8000 fps with a geforce 6600gt card. It is somewhat degraded (aprox 1-2000fps) compared to normal Xorg numbers. WHen i loaded XGL i expected some slow downs as others have stated. However, i find them minimal. How do you find it so far?

I have no lag issues with xgl..... so i am wondering if xgl is direct rendered but just not reporting it to glxinfo?

Interesting results, I seem to do way better WITH XGL.
I've had a lot of problems with 2D stuff in Windows XP, the 6600GT has some flaw with that, 3D however is done superb.

Without XGL:
> zaggynl@AMD3200L:~$ glxgears -info
GL_RENDERER   = GeForce 6600 GT/AGP/SSE2/3DNOW!
GL_VERSION    = 2.0.2 NVIDIA 87.74
GL_VENDOR     = NVIDIA Corporation
GL_EXTENSIONS = GL_ARB_color_buffer_float GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_half_float_pixel GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_texture_float GL_ATI_texture_mirror_once GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_depth_bounds_test GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_object GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_sRGB GL_EXT_timer_query GL_EXT_vertex_array GL_HP_occlusion_test GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_copy_depth_to_color GL_NV_depth_clamp GL_NV_fence GL_NV_float_buffer GL_NV_fog_distance GL_NV_fragment_program GL_NV_fragment_program_option GL_NV_fragment_program2 GL_NV_gpu_program_parameters GL_NV_half_float GL_NV_light_max_exponent GL_NV_multisample_filter_hint GL_NV_occlusion_query GL_NV_packed_depth_stencil GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_primitive_restart GL_NV_register_combiners GL_NV_register_combiners2 GL_NV_texgen_reflection GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_expand_normal GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_NV_vertex_program2 GL_NV_vertex_program2_option GL_NV_vertex_program3 GL_NVX_conditional_render GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_accum
28534 frames in 5.0 seconds = 5706.663 FPS
39391 frames in 5.0 seconds = 7878.114 FPS
42197 frames in 5.0 seconds = 8439.363 FPS
33068 frames in 5.0 seconds = 6613.537 FPS
33065 frames in 5.0 seconds = 6612.935 FPS
33080 frames in 5.0 seconds = 6615.875 FPS
32713 frames in 5.0 seconds = 6542.598 FPS
33184 frames in 5.0 seconds = 6636.702 FPS



With XGL (high results I got when having mozilla-firefox focused :/)
> zaggynl@AMD3200L:~$ glxgears -info
GL_RENDERER   = GeForce 6600 GT/AGP/SSE2/3DNOW!
GL_VERSION    = 1.2 (2.0.2 NVIDIA 87.74)
GL_VENDOR     = NVIDIA Corporation
GL_EXTENSIONS = GL_ARB_depth_texture GL_ARB_imaging GL_ARB_multitexture GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_texture_border_clamp GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_window_pos GL_ARB_texture_non_power_of_two GL_ARB_vertex_program GL_ARB_fragment_program GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_vertex_array GL_ATI_texture_mirror_once GL_HP_occlusion_test GL_IBM_texture_mirrored_repeat GL_NV_blend_square GL_NV_texgen_reflection GL_NV_texture_rectangle GL_NV_texture_env_combine4 GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow
16235 frames in 5.0 seconds = 3246.999 FPS
18565 frames in 5.0 seconds = 3710.929 FPS
18711 frames in 5.0 seconds = 3719.810 FPS
135614 frames in 5.0 seconds = 27115.311 FPS
332988 frames in 5.0 seconds = 66597.586 FPS
72828 frames in 5.0 seconds = 14524.542 FPS
18584 frames in 5.0 seconds = 3705.720 FPS
163903 frames in 5.0 seconds = 32778.750 FPS
43451 frames in 5.0 seconds = 8636.286 FPS
18582 frames in 5.0 seconds = 3702.973 FPS


With XGL & Compiz
> zaggynl@AMD3200L:~$ compiz-start
zaggynl@AMD3200L:~$ glxgears -info
GL_RENDERER   = GeForce 6600 GT/AGP/SSE2/3DNOW!
GL_VERSION    = 1.2 (2.0.2 NVIDIA 87.74)
GL_VENDOR     = NVIDIA Corporation
GL_EXTENSIONS = GL_ARB_depth_texture GL_ARB_imaging GL_ARB_multitexture GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_texture_border_clamp GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_window_pos GL_ARB_texture_non_power_of_two GL_ARB_vertex_program GL_ARB_fragment_program GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_vertex_array GL_ATI_texture_mirror_once GL_HP_occlusion_test GL_IBM_texture_mirrored_repeat GL_NV_blend_square GL_NV_texgen_reflection GL_NV_texture_rectangle GL_NV_texture_env_combine4 GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow
47606 frames in 5.0 seconds = 9507.350 FPS
52691 frames in 5.0 seconds = 10522.675 FPS
52571 frames in 5.0 seconds = 10501.724 FPS
52588 frames in 5.0 seconds = 10512.912 FPS
52702 frames in 5.0 seconds = 10523.680 FPS
51545 frames in 5.0 seconds = 10303.283 FPS
45520 frames in 5.0 seconds = 9094.975 FPS


---

### Post by DoorGunner on 2006-09-19
Thanks for the web site....I did the method B as well and it improved my results and some transparency issues i didnt notice.

john@DoorGunner:~$ glxgears
46511 frames in 5.0 seconds = 9288.649 FPS
47116 frames in 5.0 seconds = 9400.256 FPS
46871 frames in 5.0 seconds = 9368.610 FPS

I am still something short of you in terms of fps.... i am sure there is a tweek somewere for that...LOL

---

