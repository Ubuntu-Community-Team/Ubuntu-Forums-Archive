---
title: "No sound in most games."
date: 2006-07-12
forum: Gaming &amp; Leisure
---

### Post by PriceChild on 2006-07-12
Quake 4, Doom 3 and unreal tournament GOTY have no sound working :s

the previous two give the garbled output in alsa, but when forced to oss, give no sound. I'm guessing then that UT tries to give out sound in oss by default.

Please help, Pricey

---

### Post by Rosenrot on 2006-07-12
try looking at a thread i started beause i have sound issues in ut2004
[http://www.ubuntuforums.org/showthread.php?t=201855](http://www.ubuntuforums.org/showthread.php?t=201855)

ill try installing quake 4 and doom3 since i have both of those already 

i tried forcing to oss and i also got no sound
and utGOTY runs in alsa directly

but it seems like we have the same problem
ill post back later

---

### Post by Rosenrot on 2006-07-12
i installed Doom 3 and i also have no sound :/

---

### Post by Rosenrot on 2006-07-14
eh noone replies to my posts anymore :/

---

### Post by vem0m on 2006-07-14
ummmm do u have any other programs using sound? Gaim or other messengers, web browsers, or media players? as that might throw the sound out i dunno let me know

---

### Post by Polygon on 2006-07-14
from my experiences,

adding "+set s_driver oss" to the command line launcher or whatever for quake4/doom 3 makes sound work properly

and for ut2004, i had no sound also, and then someone suggested to me, entering the command

killall esd

before playing, and it worked

---

### Post by Rosenrot on 2006-07-16
> **vem0m said:**
> ummmm do u have any other programs using sound? Gaim or other messengers, web browsers, or media players? as that might throw the sound out i dunno let me know

yes i have those programs running with sound 
eg:gaim/rythombox/misc. games i have installed with synaptic (small 2d games)

but those all run with esd and i have no problems with esd

though the couple of times i have gotten sound with ut2004 gaim and other programs were running
odd

---

### Post by Rosenrot on 2006-07-16
b@b-desktop:~$ doom3 +set s_driver oss
DOOM 1.1.1286 linux-x86 Nov 24 2004 17:56:04
Hostname: b-desktop
local IP: 127.0.1.1
------ Initializing File System ------
Loaded pk4 /usr/local/games/doom3/base/game00.pk4 with checksum 0x7dafc4d4
Loaded pk4 /usr/local/games/doom3/base/game01.pk4 with checksum 0x16cf3b8a
Loaded pk4 /usr/local/games/doom3/base/pak000.pk4 with checksum 0x28d208f1
Loaded pk4 /usr/local/games/doom3/base/pak001.pk4 with checksum 0x40244be0
Loaded pk4 /usr/local/games/doom3/base/pak002.pk4 with checksum 0xc51ecdcd
Loaded pk4 /usr/local/games/doom3/base/pak003.pk4 with checksum 0xcd79d028
Loaded pk4 /usr/local/games/doom3/base/pak004.pk4 with checksum 0x765e4f8b
Loaded pk4 /usr/local/games/doom3/base/pak005.pk4 with checksum 0x8ffc3621
Current search path:
/home/b/.doom3/base
/usr/local/games/doom3/base
/usr/local/games/doom3/base/pak005.pk4 (63 files)
/usr/local/games/doom3/base/pak004.pk4 (5137 files)
/usr/local/games/doom3/base/pak003.pk4 (4676 files)
/usr/local/games/doom3/base/pak002.pk4 (6120 files)
/usr/local/games/doom3/base/pak001.pk4 (8972 files)
/usr/local/games/doom3/base/pak000.pk4 (2698 files)
/usr/local/games/doom3/base/game01.pk4 (2 files)
/usr/local/games/doom3/base/game00.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
file system initialized.
--------------------------------------
----- Initializing Decls -----
------------------------------
------- Initializing renderSystem --------
using ARB renderSystem
renderSystem initialized.
--------------------------------------
5151 strings read from strings/english.lang
Couldn't open journal files
execing editor.cfg
execing default.cfg
execing DoomConfig.cfg
couldn't exec autoexec.cfg
5151 strings read from strings/english.lang
----- Initializing Sound System ------
sound system initialized.
--------------------------------------
----- R_InitOpenGL -----
Setup X display connection
dlopen(libGL.so.1)
Initializing OpenGL display
Using XFree86-VidModeExtension Version 2.2
DGA DirectVideo Mouse (Version 2.0) initialized
Free86-VidModeExtension Activated at 1024x768
Using 8/8/8 Color bits, 8 Alpha bits, 24 depth, 8 stencil display.
GL_RENDERER: GeForce FX 5600/AGP/SSE/3DNOW!
GL_EXTENSIONS: GL_ARB_depth_texture GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_half_float_pixel GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_object GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_paletted_texture GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_shared_texture_palette GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_sRGB GL_EXT_timer_query GL_EXT_vertex_array GL_HP_occlusion_test GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_copy_depth_to_color GL_NV_depth_clamp GL_NV_fence GL_NV_float_buffer GL_NV_fog_distance GL_NV_fragment_program GL_NV_fragment_program_option GL_NV_half_float GL_NV_light_max_exponent GL_NV_multisample_filter_hint GL_NV_occlusion_query GL_NV_packed_depth_stencil GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_primitive_restart GL_NV_register_combiners GL_NV_register_combiners2 GL_NV_texgen_reflection GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_expand_normal GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_NV_vertex_program2 GL_NV_vertex_program2_option GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_accum

------- Input Initialization -------
XKB extension: compile time 0x1:0x0, runtime 0x1:0x0: OK
XKB extension present on server ( 0x1:0x0 )
------------------------------------
------ OSS Sound Initialization ------
opened sound device '/dev/dsp'
ioctl SNDCTL_SYSINFO failed: Invalid argument
this ioctl is only available in OSS/Linux implementation. If you run OSS/Free, don't bother./dev/dsp - bit rate: 16, channels: 2, frequency: 44100
allocated a mix buffer of 16384 bytes
WARNING: ioctl SNDCTL_DSP_SETTRIGGER PCM_ENABLE_OUTPUT failed: Broken pipe
--------------------------------------
...using GL_ARB_multitexture
...using GL_ARB_texture_env_combine
...using GL_ARB_texture_cube_map
...using GL_ARB_texture_env_dot3
...using GL_ARB_texture_env_add
X..GL_ARB_texture_non_power_of_two not found
...using GL_ARB_texture_compression
...using GL_EXT_texture_compression_s3tc
...using GL_EXT_texture_filter_anisotropic
   maxTextureAnisotropy: 8.000000
...using GL_1.4_texture_lod_bias
...using GL_EXT_shared_texture_palette
...using GL_EXT_texture3D
...using GL_EXT_stencil_wrap
...using GL_NV_register_combiners
...using GL_EXT_stencil_two_side
X..GL_ATI_fragment_shader not found
X..GL_ATI_text_fragment_shader not found
...using GL_ARB_vertex_buffer_object
...using GL_ARB_vertex_program
...using GL_ARB_fragment_program
X..EXT_depth_bounds_test not found
---------- R_NV20_Init ----------
---------------------------------
----------- R200_Init -----------
Not available.
---------- R_ARB2_Init ----------
Available.
Cg not available.
---------------------------------
---------- R_Exp_Init -----------
Disabled at compile time.
---------------------------------
----- R_ReloadARBPrograms -----
glprogs/test.vfp
glprogs/test.vfp
glprogs/interaction.vfp
glprogs/interaction.vfp
glprogs/bumpyEnvironment.vfp
glprogs/bumpyEnvironment.vfp
glprogs/ambientLight.vfp
glprogs/ambientLight.vfp
glprogs/shadow.vp
glprogs/R200_interaction.vp
glprogs/nv20_bumpAndLight.vp
glprogs/nv20_diffuseColor.vp
glprogs/nv20_specularColor.vp
glprogs/nv20_diffuseAndSpecularColor.vp
glprogs/environment.vfp
glprogs/environment.vfp
-------------------------------
using ARB_vertex_buffer_object memory
using ARB2 renderSystem
found DLL in pak file: /usr/local/games/doom3/base/game01.pk4/gamex86.so
copy gamex86.so to /home/b/.doom3/base/gamex86.so
--------- Initializing Game ----------
gamename: baseDOOM-1
gamedate: Oct  4 2004
Initializing event system
...472 event definitions
Initializing class hierarchy
...141 classes, 381376 bytes for event callbacks
Initializing scripts
/proc/cpuinfo CPU frequency: 1830.16 MHz
Compiled 'removeInitialSplineAngles': 2322.3 ms
---------- Compile stats ----------

Memory usage:
     Strings: 79, 12592 bytes
  Statements: 67783, 1355660 bytes
   Functions: 2108, 250452 bytes
   Variables: 147320 bytes
    Mem used: 2476244 bytes
 Static data: 2277552 bytes
   Allocated: 3283340 bytes
 Thread size: 7068 bytes

...6 aas types
game initialized.
--------------------------------------
-------- Initializing Session --------
session initialized
--------------------------------------
--- Common Initialization Complete ---
------------- Warnings ---------------
during DOOM 3 initialization...
WARNING: ioctl SNDCTL_DSP_SETTRIGGER PCM_ENABLE_OUTPUT failed: Broken pipe
1 warnings
terminal support enabled ( use +set in_tty 0 to disabled )
pid: 6434
1520 MB System Memory
guessing video ram ( use +set sys_videoRam to force ) ..
found XNVCtrl extension 1.10
256 MB Video Memory
Async thread started
idAudioHardwareOSS::Write: 1024 samples were overflowed and dropped
idAudioHardwareOSS::Write: 1024 samples were overflowed and dropped
idAudioHardwareOSS::Write: 1024 samples were overflowed and dropped
idAudioHardwareOSS::Write: 1024 samples were overflowed and dropped
idAudioHardwareOSS::Write: 1024 samples were overflowed and dropped
idAudioHardwareOSS::Write: 1024 samples were overflowed and dropped
idAudioHardwareOSS::Write: 1024 samples were overflowed and dropped
idAudioHardwareOSS::Write: 1024 samples were overflowed and dropped
idAudioHardwareOSS::Write: 1024 samples were overflowed and dropped
idAudioHardwareOSS::Write: 1024 samples were overflowed and dropped
idAudioHardwareOSS::Write: 1024 samples were overflowed and dropped
idAudioHardwareOSS::Write: 1024 samples were overflowed and dropped
idAudioHardwareOSS::Write: 1024 samples were overflowed and dropped
idAudioHardwareOSS::Write: 1024 samples were overflowed and dropped
idAudioHardwareOSS::Write: 1024 samples were overflowed and dropped
idAudioHardwareOSS::Write: 1024 samples were overflowed and dropped
idAudioHardwareOSS::Write: 1024 samples were overflowed and dropped
idAudioHardwareOSS::Write: 1024 samples were overflowed and dropped
idAudioHardwareOSS::Write: 1024 samples were overflowed and dropped
idAudioHardwareOSS::Write: 1024 samples were overflowed and dropped
idAudioHardwareOSS::Write: 1024 samples were overflowed and dropped
idAudioHardwareOSS::Write: 1024 samples were overflowed and dropped
idAudioHardwareOSS::Write: 1024 samples were overflowed and dropped
idAudioHardwareOSS::Write: 1024 samples were overflowed and dropped
idAudioHardwareOSS::Write: 1024 samples were overflowed and dropped
idAudioHardwareOSS::Write: 1024 samples were overflowed and dropped
idAudioHardwareOSS::Write: 1024 samples were overflowed and dropped
idAudioHardwareOSS::Write: 1024 samples were overflowed and dropped
idAudioHardwareOSS::Write: 1024 samples were overflowed and dropped
idAudioHardwareOSS::Write: 1024 samples were overflowed and dropped
idAudioHardwareOSS::Write: 1024 samples were overflowed and dropped
idAudioHardwareOSS::Write: 1024 samples were overflowed and dropped
idAudioHardwareOSS::Write: 1024 samples were overflowed and dropped
idAudioHardwareOSS::Write: 1024 samples were overflowed and dropped
idAudioHardwareOSS::Write: 1024 samples were overflowed and dropped
idAudioHardwareOSS::Write: 1024 samples were overflowed and dropped
idAudioHardwareOSS::Write: 1024 samples were overflowed and dropped
idAudioHardwareOSS::Write: 1024 samples were overflowed and dropped
idAudioHardwareOSS::Write: 1024 samples were overflowed and dropped
idAudioHardwareOSS::Write: 1024 samples were overflowed and dropped
idAudioHardwareOSS::Write: 1024 samples were overflowed and dropped
--------- Game Map Shutdown ----------
--------------------------------------
Shutting down sound hardware
------ OSS Sound Shutdown ------
close sound device
--------------------------------
idRenderSystem::Shutdown()
------------ Game Shutdown -----------
--------- Game Map Shutdown ----------
--------------------------------------
Shutdown event system
--------------------------------------
shutdown terminal support


OSS won't start.............

---

### Post by mjziegle on 2006-07-17
sudo /etc/init.d/bootmisc.sh stop
sudo gedit /etc/init.d/bootmisc.sh (add this just before the exit line)
 
#-----------------------
# fix sound for Quake 3 and Enemy Territory
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "quake3.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "quake3.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
#------------------------

sudo /etc/init.d/bootmisc.sh start



Worked for me.

---

### Post by vem0m on 2006-07-17
what i meant was do u have any of them things running when u are trying to load the game up?

---

### Post by PriceChild on 2006-07-17
> **mjziegle said:**
> Add these lines to you /etc/init.d/bootmisc.sh file before the exit line.
sudo /etc/init.d/bootmisc.sh stop
sudo /etc/init.d/bootmisc.sh start

Worked for me.

Not sure about changing this... looks pretty dodgy, making the script stop itself..... meaning it won't start again? :S

Can anyone comment on this please? Pricey

---

### Post by vem0m on 2006-07-17
looks wierd to me on the baisis it looks like the dude is trying to tell u to make it stop then start again right after it? don't make any kind of sense

---

### Post by PriceChild on 2006-07-17
Especially as this is about the boot process... and not about sound really :s

---

### Post by Rosenrot on 2006-07-17
> **vem0m said:**
> what i meant was do u have any of them things running when u are trying to load the game up?

I said i did have them running the only couple of times ive started ut2004

and when all other programs are closed or I start ut2004 immediatley after loggin on there is no sound

I guess i should of made it clearer

---

### Post by vem0m on 2006-07-17
hmmmm i am out ideas then sadly and thx for clearifying :)

---

### Post by Rosenrot on 2006-07-17
> **vem0m said:**
> hmmmm i am out ideas then sadly and thx for clearifying :)

its ok
thanks for helping
not many people do anymore now

ive pretty much given up on linux gaming for the time being
ill just stick to my windows machine for gaming intill i figure out a way to get it working in ubuntu

ive spent about 3or 4 weeks on this problem

---

### Post by mjziegle on 2006-07-19
> **PriceChild said:**
> Not sure about changing this... looks pretty dodgy, making the script stop itself..... meaning it won't start again? :S

Can anyone comment on this please? Pricey

You start and stop the script because you made changes and you want the changes to take place without having to reboot.  Would you have questioned the instructions if I said reboot instead.

ID games need to directly access OSS.  All these lines tell the system to do is give quake3 direct access to OSS.  Putting it in the bootmisc.sh (a script for little odds and ends) just makes the process easier.  

Maybe I should have been more clear.


Good luck.

---

### Post by PriceChild on 2006-07-19
> **mjziegle said:**
> You start and stop the script because you made changes and you want the changes to take place without having to reboot.  Would you have questioned the instructions if I said reboot instead.

ID games need to directly access OSS.  All these lines tell the system to do is give quake3 direct access to OSS.  Putting it in the bootmisc.sh (a script for little odds and ends) just makes the process easier.  

Maybe I should have been more clear.


Good luck.

Yeah but this script is run at boot.... and you haven't told me to make any other changes anyway ^o)

---

### Post by guine on 2006-07-19
Do you have onboard sound in addition to a sound card?  I didnt have sound for most of my games until I disabled my onboard sound.

---

### Post by PriceChild on 2006-07-19
onboard only

---

### Post by mjziegle on 2006-07-19
> **PriceChild said:**
> Yeah but this script is run at boot.... and you haven't told me to make any other changes anyway ^o)

I told you to add these lines to bootmisc.sh

#-----------------------
# fix sound for Quake 3 and Enemy Territory
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "quake3.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "quake3.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
#------------------------

then restart it.  ????

---

### Post by DoktorSeven on 2006-07-19
Argh.  No sound in gaming means usually the game's trying to directly access a soundcard that doesn't support hardware mixing through your sound system (ALSA/OSS).

Shut down anything that makes sound, kill esd (for Gnome) or artsd (for KDE), and try again.

---

### Post by hotani on 2006-07-26
I tried the Doom3 and Quake4 demos last night and was met with garbled sound in both.

I'm reading through this thread and thinking: this is a helluva lot of work to go through (messing with low level system settings - Yikes.) to get sound for a computer game. I'll start with the simple fixes tonight and see if it helps. My sound is on-board btw - on a Gigabyte M-55 AM2 board.

---

