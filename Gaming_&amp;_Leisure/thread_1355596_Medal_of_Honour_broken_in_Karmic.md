---
title: "Medal of Honour broken in Karmic ?"
date: 2009-12-15
forum: Gaming &amp; Leisure
---

### Post by itoffshore on 2009-12-15
[COLOR="Red"]** Update ** - regressing back to Linux Mint 6 (intrepid 8.10) fixed the problem so there is a problem in the new xorg-intel drivers in Karmic. I just needed to add the following symlink:

```

sudo ln -s /usr/lib/libGL.so.1 /usr/lib/libGL.so

```

The new drivers in 9.10 with GEM support in the kernel also break Sauerbraten & Blood Frontier:[/COLOR]

[http://sourceforge.net/apps/phpbb/bloodfrontier/viewtopic.php?f=3&t=76]("http://sourceforge.net/apps/phpbb/bloodfrontier/viewtopic.php?f=3&t=76")

[COLOR="Red"]Reverting back fixed these problems too.

From a gaming point of view there is no benefit to running 9.10 currently. In both 8.10 & 9.10 I get around 60 FPS in Urban Terror except 9.10 shows occasionally white glitches on the screen.[/COLOR]
==========================================================================

Medal of Honour Allied Assault seems to be broken in Ubuntu Karmic (it worked fine in Hardy / Hardy with a Jaunty kernel)

I tried installing the game again (this requires libgtk-1.2 packages from Jaunty to be installed which are deprecated in Karmic as it uses libgtk-2.0) - the game menu loads ok & has sound but as soon as you load a level the loading progress bar doesn't move & the game crashes without any meaningful error messages. This seems to be a duplicate of this old bug [https://bugzilla.icculus.org/show_bug.cgi?id=1305](https://bugzilla.icculus.org/show_bug.cgi?id=1305)

The cause of the problem doesn't seem to be related to the openal messages shown below as if I create a symlink in the game directory to /usr/lib/libopenal.so.0 (or .1) I get errors about missing Loki extenstions when the sound library is loaded.

libGL seems to be loading properly - when I ran Hardy with a Jaunty kernel the game was completable on single player so it can't be the new Xorg-Intel drivers which use EXA instead of UXA (or maybe it is a driver problem). Are there any other libraries called by fgame.so which are now no longer on my Karmic system which could be fixed with some symlinks ? (doing this fixed Smokin'Guns & TrueCombat:Elite after the move to Karmic) - as when fgame.so is loaded is when the game crashes.

My video card is an Intel G965M & I'm running the 2.6.31-16 kernal on Xubuntu Karmic 

I've attached the output of strace if anyone can make any sense of it (I've not used it before)

Stuart.

```

--- Common Initialization ---
Medal of Honor Allied Assault 1.11 linux-i386 Sep  3 2004
----- FS_Startup -----
Current search path:
/home/stuart/.mohaa/main
/home/stuart/Games/mohaa/main
/home/stuart/Games/mohaa/main/pak6.pk3 (104 files)
/home/stuart/Games/mohaa/main/pak5.pk3 (259 files)
/home/stuart/Games/mohaa/main/pak4.pk3 (593 files)
/home/stuart/Games/mohaa/main/pak3.pk3 (669 files)
/home/stuart/Games/mohaa/main/pak2.pk3 (4722 files)
/home/stuart/Games/mohaa/main/pak1.pk3 (772 files)
/home/stuart/Games/mohaa/main/pak0.pk3 (11175 files)

----------------------
18294 files in pk3 files
execing default.cfg
execing menu.cfg
couldn't exec newconfig.cfg
Config: unnamedsoldier.cfg
STUB: wtf in unix/linux_general_extras.c line 95.
STUB: wtf in unix/linux_general_extras.c line 101.
execing configs/unnamedsoldier.cfg
couldn't exec localized.cfg
execing autoexec.cfg
Unknown command "fov"
couldn't exec custom.cfg
You are now setup for easy mode.
----- Client Initialization -----
Called FadeSound with: 0.000000
----- Initializing Renderer ----
----- R_Init -----
...loading libGL.so: Initializing SDL OpenGL display
...setting mode 3: 640 480
Attempting 4/4/4 Color bits, 24 depth, 0 stencil display...
Xlib:  extension "XiG-SUNDRY-NONSTANDARD" missing on display ":0.0".
STUB: missing hardware detection in unix/linux_glimp_sdl.c line 985.
Initializing OpenGL extensions
...GL_S3_s3tc not found
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array

GL_VENDOR: Tungsten Graphics, Inc
GL_RENDERER: Mesa DRI Intel(R) 965GM GEM 20090712 2009Q2 RC3 x86/MMX/SSE2
GL_VERSION: 2.1 Mesa 7.6
GL_EXTENSIONS: [...omitted...]
GL_MAX_TEXTURE_SIZE: 4096
GL_MAX_ACTIVE_TEXTURES_ARB: 8

PIXELFORMAT: color(16-bits) Z(24-bit) stencil(0-bits)
MODE: 3, 640 x 480 fullscreen hz:N/A
GAMMA: software w/ 0 overbright bits
CPU: 
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 1
texture bits: 16
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: disabled
Initializing Shaders
Setting up Shaders
----- finished R_Init -----
------- profiling DrawBackground methods -------
glDrawPixels w/ BGR: 0 clocks
glDrawPixels w/ RGB: 0 clocks
glTexSubImage2D w/ BGR: 0 clocks
glTexSubImage2D w/ RGB: 0 clocks
DrawBackground: using glDrawPixels with BGR data
-------------------------------
Opening IP socket: localhost:12203
Hostname: stuart-laptop
IP: 127.0.1.1
------- Sound Initialization (full) -------
OpenAL: Opening device {default}...
OpenAL: Device opened successfully.
OpenAL: Creating AL context...
OpenAL: Context created successfully.
AL_VENDOR: J. Valenzuela
AL_VERSION: 0.0.7
AL_RENDERER: Software
AL_EXTENSIONS: AL_LOKI_quadriphonic AL_LOKI_play_position AL_LOKI_WAVE_format AL_LOKI_IMA_ADPCM_format AL_LOKI_buffer_data_callback ALC_LOKI_audio_channel 
AL extension: Looking up required symbol "alutLoadMP3_LOKI"......found.
AL extension: Looking up symbol "alReverbScale_LOKI"......found.
AL extension: Looking up symbol "alReverbDelay_LOKI"......found.
Loading global/sound0.txt
------- S_StopAllSounds (stop music) -------
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
------- S_StopAllSounds Complete-------
----- Sound Info -----
device - {default}
reverb - OFF
samplebits - 16
speed - 11025
----------------------
------- Sound Initialization Complete ------- 11 ms
Setting up Shaders
Loading inventory...
----- Client Initialization Complete ----- 1473 ms
--- Common Initialization Complete --- 1923 ms
--- Localization: I see 0 localization files
--- Localization: reading file global/localization.txt
Loading Localization File global/localization.txt
Loaded 1242 localization entries
------- Sound Initialization (full) -------
Cmd_AddCommand: play already defined
Cmd_AddCommand: soundlist already defined
Cmd_AddCommand: soundinfo already defined
Cmd_AddCommand: sounddump already defined
------- S_StopAllSounds (stop music) -------
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
------- S_StopAllSounds Complete-------
----- Sound Info -----
device - {default}
reverb - OFF
samplebits - 16
speed - 11025
----------------------
------- Sound Initialization Complete ------- 0 ms
------- S_StopAllSounds (stop music) -------
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
------- S_StopAllSounds Complete-------
STUB: sample_offset in client/snd_openal_new.cpp line 3867.
FIXME: Allow reverb toggle at runtime in OpenAL code.
You are now setup for easy mode.
------ Server Initialization ------
Server: briefing/briefing2
Called FadeSound with: 0.000000
Called FadeSound with: 0.000000
------- S_StopAllSounds (stop music) -------
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
------- S_StopAllSounds Complete-------
------- S_StopAllSounds (stop music) -------
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
------- S_StopAllSounds Complete-------
Called FadeSound with: 0.000000
Setting up Shaders
UI_DrawConnect called
------ Unloading fgame.so ------
------- Attempting to load ./fgame.so -------
----- CL_Shutdown -----
Called FadeSound with: 0.000000
------- S_StopAllSounds (stop music) -------
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
------- S_StopAllSounds Complete-------
------- Sound Shutdown (full) -------
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
STUB: sample_ms_offset in client/snd_openal_new.cpp line 3824.
OpenAL: Destroying channels...
OpenAL: Channels destroyed successfully.
OpenAL: Destroying context...
OpenAL: Context destroyed successfully.
OpenAL: Closing device...
OpenAL: Device closed successfully.
------- Sound Shutdown Complete -------
RE_Shutdown( 1 )
-----------------------

```

---

