---
title: "Gaming on laptop with intel 915gm graphics chipset?"
date: 2006-04-15
forum: Gaming &amp; Leisure
---

### Post by rorschach on 2006-04-15
Is this even possible?
My laptop will run games handily in that other operating system, however, I am unable to play WoW or even Warcraft III in linux. I have been reading through the forums, and I see that there are a number of people that are able to play these games on their systems, but it seems that these are all on Nvidia or ATI cards.

Am I wasting my time here? Should I just set up my system to dual-boot?


FYI I have reloaded my laptop no less than twice daily for the last few weeks. I have tried a number of the snapshot loads from dri.freedesktop.org, I have tied different versions of wine, I have tried moving to Dapper... all with varying degrees of failure.
I have had the greatest degree of success by installing wine 0.9.12 and loading Warcraft III - it runs, but only in d3d mode (opengl gives a black screen, sound is good though). Even under D3d mode, I have boxes all over the place that finally render if the screen stops moving, the sound is almost unlistenable because of this.

Upon completion of default install of Breezy - glxinfo shows that direct rendering is yes, lsmod shows that my module is being recognizes by the kernel (i915), and xorg.conf is calling the i810 module... all like the various threads around the Ubuntu forums (and some from the web) say that it should be.
When I try to install a dri snapshot, following their directions, opengl stops recognizing my module and drops to direct rendering = no, and I lose even the (apparently empty) promise of opengl rendering, failing over to indirect emulation.

Am I doing something wrong? or is this graphics chipset just a no-go for Linux overall?

---

### Post by sorcererx84 on 2006-04-15
Try the 20060107 snapshot. I am using it and glxgears gives me about 1200 fps. I can even play ut2004 in opengl mode with some of the options turned to low. Warcraft 3 works perfectly.

---

### Post by rorschach on 2006-04-15
Thank you for the pointer.
I'm not seeing 20060107 in the snapshots - not even in the archive.

I'm willing to try others, however, like I said, everytime I try, opengl stops recognizing my video driver - any pointers on how you did your build/install? Maybe I'm doing it wrong.

---

### Post by rorschach on 2006-04-16
after some research, if what I am reading is true - all of the new snapshots from dri.freedesktop.org are for xorg 6.9 and 7.0, which is not on breezy.

Any clues or links to the older snapshots?

---

### Post by rorschach on 2006-04-16
Well, I downloaded and installed the common, i810, and i915 drivers from dri.freedesktop.org/snapshots. I got no errors this time, and here's my output from glxinfo and lsmod```
derrick@anubis:~/.wine/drive_c/Warcraft III$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method,
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control,
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGIS_multisample,
    GLX_SGIX_fbconfig
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 915GM 20050225 x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 6.3
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_imaging,
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_point_parameters,
    GL_ARB_shadow, GL_ARB_texture_border_clamp, GL_ARB_texture_compression,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle,
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object,
    GL_ARB_vertex_program, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra,
    GL_EXT_blend_color, GL_EXT_blend_equation_separate,
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract,
    GL_EXT_clip_volume_hint, GL_EXT_cull_vertex, GL_EXT_compiled_vertex_array,
    GL_EXT_convolution, GL_EXT_copy_texture, GL_EXT_draw_range_elements,
    GL_EXT_fog_coord, GL_EXT_histogram, GL_EXT_multi_draw_arrays,
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_polygon_offset,
    GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap,
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias,
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array,
    GL_3DFX_texture_compression_FXT1, GL_APPLE_client_storage,
    GL_APPLE_packed_pixels, GL_ATI_blend_equation_separate,
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat,
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_ycbcr_texture,
    GL_MESA_window_pos, GL_NV_blend_square, GL_NV_light_max_exponent,
    GL_NV_texture_rectangle, GL_NV_texgen_reflection, GL_NV_vertex_program,
    GL_NV_vertex_program1_1, GL_OES_read_format, GL_SGI_color_matrix,
    GL_SGI_color_table, GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture,
    GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
derrick@anubis:~/.wine/drive_c/Warcraft III$ lsmod
Module                  Size  Used by
nls_cp437               5664  1
isofs                  35960  1
udf                    90820  0
rfcomm                 38460  0
l2cap                  24740  5 rfcomm
speedstep_centrino      7636  1
cpufreq_userspace       4316  1
cpufreq_stats           5252  0
freq_table              4388  2 speedstep_centrino,cpufreq_stats
cpufreq_powersave       1696  0
cpufreq_ondemand        6044  0
cpufreq_conservative     6948  0
pcmcia                 26568  2
video                  15748  0
tc1100_wmi              6692  0
sony_acpi               5324  0
pcc_acpi               11104  0
hotkey                  9284  0
dev_acpi               11108  0
i2c_acpi_ec             5472  0
i2c_core               21200  1 i2c_acpi_ec
button                  6480  0
battery                 9348  0
container               4384  0
ac                      4708  0
i915                   21760  3
drm                    74104  4 i915
ipv6                  251232  6
af_packet              21768  2
rtc                    12344  0
pcspkr                  3396  0
irtty_sir               8512  0
sir_dev                18444  1 irtty_sir
irda                  187612  2 irtty_sir,sir_dev
crc_ccitt               1984  1 irda
hci_usb                14088  2
bluetooth              48356  7 rfcomm,l2cap,hci_usb
yenta_socket           25292  1
rsrc_nonstatic         13376  1 yenta_socket
pcmcia_core            49348  3 pcmcia,yenta_socket,rsrc_nonstatic
ipw2200               103880  0
firmware_class          9952  1 ipw2200
ieee80211              29380  1 ipw2200
ieee80211_crypt         5604  2 ipw2200,ieee80211
tpm_nsc                 6656  0
tpm                     9888  1 tpm_nsc
snd_intel8x0           33248  1
snd_ac97_codec         83932  1 snd_intel8x0
snd_pcm_oss            52704  0
snd_mixer_oss          19296  1 snd_pcm_oss
snd_pcm                88840  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              24164  1 snd_pcm
snd                    54884  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9600  1 snd
snd_page_alloc         10600  2 snd_intel8x0,snd_pcm
pci_hotplug            27508  0
intel_agp              23164  1
agpgart                34792  3 drm,intel_agp
dm_mod                 57692  1
joydev                  9984  0
tsdev                   7776  0
evdev                   9664  1
psmouse                30116  0
mousedev               11616  1
parport_pc             35236  1
lp                     12292  0
parport                35912  2 parport_pc,lp
md                     45584  0
ext3                  136264  2
jbd                    54776  1 ext3
mbcache                 9252  1 ext3
thermal                13000  0
processor              22812  2 speedstep_centrino,thermal
fan                     4484  0
tg3                    96772  0
ehci_hcd               34248  0
uhci_hcd               31184  0
usbcore               118044  4 hci_usb,ehci_hcd,uhci_hcd
ide_cd                 41572  1
cdrom                  39616  1 ide_cd
ide_disk               18464  4
ide_generic             1376  0
piix                   10372  1
ide_core              138772  4 ide_cd,ide_disk,ide_generic,piix
unix                   26896  699
fbcon                  38496  0
tileblit                2368  1 fbcon
font                    8224  1 fbcon
bitblit                 5632  1 fbcon
vesafb                  7992  0
cfbcopyarea             4608  1 vesafb
cfbimgblt               2944  1 vesafb
cfbfillrect             3872  1 vesafb
softcursor              2272  1 vesafb
capability              4712  0
commoncap               6816  1 capability
derrick@anubis:~/.wine/drive_c/Warcraft III$

```

When I try to launch wine war3.exe -opengl - its sounds great!... and I have a blank screen.

from what I am seeing, glxinfo isn't seeing my new driver, right?
How do I fix this?

*note - perhaps this falls under the Hardware section - is it possible to move this thread there?

---

### Post by sorcererx84 on 2006-04-18
It is seeing your driver - OpenGL renderer string: Mesa DRI Intel(R) 915GM 20050225 x86/MMX/SSE2
Try glxgears -printfps. If your FPS is over 1000 you have 3D acceleration working and Warcraft or Wine is causing your problem.

---

### Post by rorschach on 2006-04-18
well, I am getting around 1260fps in the little window for glxgears...
however, I am still getting a blank screen when I try to launch Warcraft III with the -opengl tag.

I'm considering giving Cedega another shot... or just skipping to WoW and seeing if it runs (I was kinda using Warcraft three as a 'benchmark' for the few games I like).

Are there, maybe, any *other* games that are similar to Warcraft III that I could try out? Heck, I still play Starcraft on occasion, if that could be loaded.

---

### Post by sorcererx84 on 2006-04-19
Your direct rendering is OK, check your configuration. I can run Warcraft 3 almost perfectly on my laptop with i915gm integrated graphics card.

---

### Post by rorschach on 2006-04-19
Here's the thing - if I try to launch without the -opengl tag, it launches, but is horribly choppy, this is a known issue with d3d, I think. However, when I launch *with* the -opengl tag, it does not bring up a display. I have set up my winecfg with windows2000, the cdrom is being seen correctly, however, when I try to access the sound tab, winecfg dies.

I'll try again tonight

---

### Post by rorschach on 2006-04-20
I give for now - no change.
Still getting choppy video/sound (to an unplayable level) in d3d mode, and opengl gives a blank black screen that sounds great, but nothing ever shows on the screen.

Unless someone has something else I can check, I feel somewhat stymied at this point, and am somewhat resigned to not being able to get Warcraft III to play.

I figure I must be doing something wrong, since you seem to have it working sorcererx84, but I don't know what! I feel like I have checked everything 5 or more times and it just.doesn't.work.

---

### Post by Sector on 2006-09-19
This is so frustrating, I have _exactly_ the same problem as rorschach, 1100+ fps on glxgears, 3D seems to be functioning. But in Warcraft III I get extremely low fps in D3D mode. And the -opengl mode is just a black screen (with good sound though).

I sincerely hope some guru could provide me (and rorschach) with some enlightenment on this issue. Thanks in advance.

---

### Post by Kelsin on 2006-09-22
I have the same issue. In opengl mode the game "runs" but just with a black screen. I read on some random forum that you need newer DRI drivers... but haven't tried to update mine yet. I'm hoping the package will update soon and solve it for me :)

---

### Post by prowler on 2007-05-07
Same here: [http://ubuntuforums.org/showthread.php?t=409674](http://ubuntuforums.org/showthread.php?t=409674)

---

