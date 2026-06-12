---
title: "Wolf Et on Ubuntu 11.04"
date: 2011-07-11
forum: Gaming &amp; Leisure
---

### Post by Draken2910 on 2011-07-11
My system specs dunno if its needed.

AMD Phenom II X4 955 Black Edition Deneb 3.2GHz Socket AM3
SAPPHIRE TOXIC 100282TXSR Radeon HD 5850 1GB
CORSAIR XMS3 4GB (2 x 2GB) 240-Pin DDR3 SDRAM DDR3 1333
GIGABYTE GA-MA790GPT-UD3H AM3 AMD 790GX HDMI ATX AMD


Below this is a guide that I myself have created to get ET to run, and get it to play with sound on Ubuntu 11.04
It took close to 4 hours for me to dig through figure what was wrong and fix it and get it up to speed, also to play steadly without punkbuster kicking you.

Installation of ET

Step .5 : Smash your face in the keyboard

Step one : get Wolfenstein ET for linux [http://www.fileplanet.com/124801/120000/fileinfo/Return-to-Castle-Wolfenstein:-Enemy-Territory-Client-v2.60-%5BLinux%5D](http://www.fileplanet.com/124801/120000/fileinfo/Return-to-Castle-Wolfenstein:-Enemy-Territory-Client-v2.60-%5BLinux%5D)

Step two : Once downloaded right-click on the file and goto ¨Properties¨, then from there goto ¨Permissions¨ then make sure the box ¨Allow executing of file as executable¨ is checked.

Step three : Double-Click on the file and then run it ¨In Terminal¨ follow the instructions etc.

Step four : After you are finished run the program and do a check. In the in game terminal press ~ to bring up the console, then type /pb_cdkeyreg. If you get an error some thing like ¨File Transfer Error¨ or something of that nature. We need to change the Permission

Step five : Open the terminal type cd ~, the next line type in ¨sudo chown -R user:group .etwolf¨ (replace user:group) example (sudo chown -R CaptainD:CaptainD .etwolf). In the terminal you should see the permissions change to your user.

Step six : Launch the game and type in ¨/pb_cdkeyreg¨, should say registration complete. Exit the game again.

Step seven : goto your /home then ¨Ctrl+H¨ if your folders are hidden again. navigate to your .etwolf folder. Inside it you will find your ETmain folder with your PB key in it. Delete the pbkey. Restart the game.

Step eight : Mission Complete.

Now I dont know how many of this problem effects but when i launched my game I got no sound. There are more steps to fix it down below.

Step one : Open a Terminal and type ¨sudo wget -q -O - [http://nullkey.kapsi.fi/et-sdl-sound/et-sdl-sound.gz](http://nullkey.kapsi.fi/et-sdl-sound/et-sdl-sound.gz) | gzip -d > et-sdl-sound && chmod a+x et-sdl-sound¨

Step two : Now you can start Enemy Territory with SDL sound support by running ./et-sdl-sound. Should fix it if it doesnt work just leave a post and ill try to answer the best I can.

Step three (optional) : Creating a Launcher for your Desktop. Right click your desktop then select Create Launcher. Then if you wish to change the icon, just navigate to ¨/usr/local/games/enemy-territory¨ (default install). and select the ¨et.xpm¨ file. Then in the Command type : ./et-sdl-sound

Once again if you run into any problems or have any questions leave them below. Once again these steps worked for me so I dont know if it will work for everyone. I also have searched for this complete guide in the forums but came up with no results

Thanks

**DRC**CaptainD
(Copied from my ET clans site, It is still my guide but under a different username)

---

### Post by jechill on 2011-09-15
i have 11.04 and im trying to get wolfet to have sound
the game runs great good graphics i can connect to server everything is fine but no sound
ive tried everything posted still nothing
------- sound initialization -------
[COLOR="Red"]/dev/dsp: No such file or directory
Could not open /dev/dsp[/COLOR]
------------------------------------
Sound memory manager started
Sys_LoadDll(/home/owner/.etwolf/etmain/ui.mp.i386.so)... 
Sys_LoadDll(/home/owner/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/owner/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xac68bf40  
Sys_LoadDll(ui) succeeded!
^3WARNING: Couldn't find image for shader ui/assets/icon_jaymod
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: owner-desktop
IP: 127.0.1.1
Started tty console (use +set ttycon 0 to disable)
Resolving etmaster.idsoftware.com
etmaster.idsoftware.com resolved to 192.246.40.60:27951
RE_Shutdown( 1 )
Hunk_Clear: reset the hunk ok
----- Initializing Renderer ----
-------------------------------
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 6: 1024 768
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 1024x768
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: GeForce 7025 / nForce 630a/PCI/SSE2/3DNOW!
Initializing OpenGL extensions
...using GL_S3_s3tc
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...ignoring GL_NV_fog_distance
...ignoring GL_EXT_texture_filter_anisotropic
Initializing GLX extensions
...using GLX_SGI_swap_control
...using GLX_SGI_video_sync
XF86 Gamma extension initialized


PIXELFORMAT: color(24-bits) Z(24-bit) stencil(0-bits)
MODE: 6, 1024 x 768 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_LINEAR
picmip: 0
texture bits: 0
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: enabled
anisotropy: 1.0
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----
Sys_LoadDll(/home/owner/.etwolf/etmain/ui.mp.i386.so)... 
Sys_LoadDll(/home/owner/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/owner/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xac68bf40  
Sys_LoadDll(ui) succeeded!
^3WARNING: Couldn't find image for shader ui/assets/icon_jaymod
Resolving etmaster.idsoftware.com
etmaster.idsoftware.com resolved to 192.246.40.60:27951
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Shutdown tty console
owner@owner-desktop:~$ et
ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/owner/.etwolf/etmain/~~~~~~~~~~funboymenu9A.pk3 (6 files)
/home/owner/.etwolf/etmain/SuperGoldrush_Final.pk3 (170 files)
/home/owner/.etwolf/etmain/caen2.pk3 (85 files)
/home/owner/.etwolf/etmain/baserace_desert.pk3 (154 files)
/home/owner/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

----------------------
4178 files in pk3 files
execing default.cfg
couldn't exec language.cfg
execing profiles/Chill/etconfig.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 6: 1024 768
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 1024x768
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: GeForce 7025 / nForce 630a/PCI/SSE2/3DNOW!
Initializing OpenGL extensions
...using GL_S3_s3tc
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...ignoring GL_NV_fog_distance
...ignoring GL_EXT_texture_filter_anisotropic
Initializing GLX extensions
...using GLX_SGI_swap_control
...using GLX_SGI_video_sync
XF86 Gamma extension initialized


PIXELFORMAT: color(24-bits) Z(24-bit) stencil(0-bits)
MODE: 6, 1024 x 768 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_LINEAR
picmip: 0
texture bits: 0
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: enabled
anisotropy: 1.0
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----

------- sound initialization -------
/dev/dsp: No such file or directory
Could not open /dev/dsp
------------------------------------
Sound memory manager started
Sys_LoadDll(/home/owner/.etwolf/etmain/ui.mp.i386.so)... 
Sys_LoadDll(/home/owner/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/owner/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xac807f40  
Sys_LoadDll(ui) succeeded!
^3WARNING: Couldn't find image for shader ui/assets/icon_jaymod
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: owner-desktop
IP: 127.0.1.1
Started tty console (use +set ttycon 0 to disable)
Resolving etmaster.idsoftware.com
etmaster.idsoftware.com resolved to 192.246.40.60:27951
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Shutdown tty console
owner@owner-desktop:~$ sudo wget -q -O - [http://nullkey.kapsi.fi/et-sdl-sound/et-sdl-sound.gz](http://nullkey.kapsi.fi/et-sdl-sound/et-sdl-sound.gz) | gzip -d > et-sdl-sound && chmod a+x et-sdl-sound
[sudo] password for owner: 
owner@owner-desktop:~$ /et-sdl-sound
bash: /et-sdl-sound: No such file or directory
owner@owner-desktop:~$ et
ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/owner/.etwolf/etmain/~~~~~~~~~~funboymenu9A.pk3 (6 files)
/home/owner/.etwolf/etmain/SuperGoldrush_Final.pk3 (170 files)
/home/owner/.etwolf/etmain/caen2.pk3 (85 files)
/home/owner/.etwolf/etmain/baserace_desert.pk3 (154 files)
/home/owner/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

----------------------
4178 files in pk3 files
execing default.cfg
couldn't exec language.cfg
execing profiles/Chill/etconfig.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 6: 1024 768
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 1024x768
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: GeForce 7025 / nForce 630a/PCI/SSE2/3DNOW!
Initializing OpenGL extensions
...using GL_S3_s3tc
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...ignoring GL_NV_fog_distance
...ignoring GL_EXT_texture_filter_anisotropic
Initializing GLX extensions
...using GLX_SGI_swap_control
...using GLX_SGI_video_sync
XF86 Gamma extension initialized

PIXELFORMAT: color(24-bits) Z(24-bit) stencil(0-bits)
MODE: 6, 1024 x 768 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_LINEAR
picmip: 0
texture bits: 0
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: enabled
anisotropy: 1.0
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----

------- sound initialization -------
/dev/dsp: No such file or directory
Could not open /dev/dsp
------------------------------------
Sound memory manager started
Sys_LoadDll(/home/owner/.etwolf/etmain/ui.mp.i386.so)... 
Sys_LoadDll(/home/owner/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/owner/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xac764f40  
Sys_LoadDll(ui) succeeded!
^3WARNING: Couldn't find image for shader ui/assets/icon_jaymod
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: owner-desktop
IP: 127.0.1.1
Started tty console (use +set ttycon 0 to disable)
Resolving etmaster.idsoftware.com
etmaster.idsoftware.com resolved to 192.246.40.60:27951
----- CL



i have deleted the gl stuff about the video cause it works
but the sound says no such file 
maybe this is the problem?

---

### Post by jechill on 2011-09-15
i have 11.04 and im trying to get wolfet to have sound
the game runs great good graphics i can connect to server everything is fine but no sound
ive tried everything posted still nothing
------- sound initialization -------
[COLOR="Red"]/dev/dsp: No such file or directory
Could not open /dev/dsp[/COLOR]
------------------------------------
Sound memory manager started
Sys_LoadDll(/home/owner/.etwolf/etmain/ui.mp.i386.so)... 
Sys_LoadDll(/home/owner/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/owner/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xac68bf40  
Sys_LoadDll(ui) succeeded!
^3WARNING: Couldn't find image for shader ui/assets/icon_jaymod
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: owner-desktop
IP: 127.0.1.1
Started tty console (use +set ttycon 0 to disable)
Resolving etmaster.idsoftware.com
etmaster.idsoftware.com resolved to 192.246.40.60:27951
RE_Shutdown( 1 )
Hunk_Clear: reset the hunk ok
----- Initializing Renderer ----
-------------------------------
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 6: 1024 768
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 1024x768
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: GeForce 7025 / nForce 630a/PCI/SSE2/3DNOW!
Initializing OpenGL extensions
...using GL_S3_s3tc
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...ignoring GL_NV_fog_distance
...ignoring GL_EXT_texture_filter_anisotropic
Initializing GLX extensions
...using GLX_SGI_swap_control
...using GLX_SGI_video_sync
XF86 Gamma extension initialized


PIXELFORMAT: color(24-bits) Z(24-bit) stencil(0-bits)
MODE: 6, 1024 x 768 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_LINEAR
picmip: 0
texture bits: 0
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: enabled
anisotropy: 1.0
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----
Sys_LoadDll(/home/owner/.etwolf/etmain/ui.mp.i386.so)... 
Sys_LoadDll(/home/owner/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/owner/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xac68bf40  
Sys_LoadDll(ui) succeeded!
^3WARNING: Couldn't find image for shader ui/assets/icon_jaymod
Resolving etmaster.idsoftware.com
etmaster.idsoftware.com resolved to 192.246.40.60:27951
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Shutdown tty console
owner@owner-desktop:~$ et
ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/owner/.etwolf/etmain/~~~~~~~~~~funboymenu9A.pk3 (6 files)
/home/owner/.etwolf/etmain/SuperGoldrush_Final.pk3 (170 files)
/home/owner/.etwolf/etmain/caen2.pk3 (85 files)
/home/owner/.etwolf/etmain/baserace_desert.pk3 (154 files)
/home/owner/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

----------------------
4178 files in pk3 files
execing default.cfg
couldn't exec language.cfg
execing profiles/Chill/etconfig.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 6: 1024 768
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 1024x768
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: GeForce 7025 / nForce 630a/PCI/SSE2/3DNOW!
Initializing OpenGL extensions
...using GL_S3_s3tc
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...ignoring GL_NV_fog_distance
...ignoring GL_EXT_texture_filter_anisotropic
Initializing GLX extensions
...using GLX_SGI_swap_control
...using GLX_SGI_video_sync
XF86 Gamma extension initialized


PIXELFORMAT: color(24-bits) Z(24-bit) stencil(0-bits)
MODE: 6, 1024 x 768 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_LINEAR
picmip: 0
texture bits: 0
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: enabled
anisotropy: 1.0
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----

------- sound initialization -------
/dev/dsp: No such file or directory
Could not open /dev/dsp
------------------------------------
Sound memory manager started
Sys_LoadDll(/home/owner/.etwolf/etmain/ui.mp.i386.so)... 
Sys_LoadDll(/home/owner/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/owner/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xac807f40  
Sys_LoadDll(ui) succeeded!
^3WARNING: Couldn't find image for shader ui/assets/icon_jaymod
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: owner-desktop
IP: 127.0.1.1
Started tty console (use +set ttycon 0 to disable)
Resolving etmaster.idsoftware.com
etmaster.idsoftware.com resolved to 192.246.40.60:27951
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Shutdown tty console
owner@owner-desktop:~$ sudo wget -q -O - [http://nullkey.kapsi.fi/et-sdl-sound/et-sdl-sound.gz](http://nullkey.kapsi.fi/et-sdl-sound/et-sdl-sound.gz) | gzip -d > et-sdl-sound && chmod a+x et-sdl-sound
[sudo] password for owner: 
owner@owner-desktop:~$ /et-sdl-sound
bash: /et-sdl-sound: No such file or directory
owner@owner-desktop:~$ et
ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/owner/.etwolf/etmain/~~~~~~~~~~funboymenu9A.pk3 (6 files)
/home/owner/.etwolf/etmain/SuperGoldrush_Final.pk3 (170 files)
/home/owner/.etwolf/etmain/caen2.pk3 (85 files)
/home/owner/.etwolf/etmain/baserace_desert.pk3 (154 files)
/home/owner/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

----------------------
4178 files in pk3 files
execing default.cfg
couldn't exec language.cfg
execing profiles/Chill/etconfig.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 6: 1024 768
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 1024x768
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: GeForce 7025 / nForce 630a/PCI/SSE2/3DNOW!
Initializing OpenGL extensions
...using GL_S3_s3tc
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...ignoring GL_NV_fog_distance
...ignoring GL_EXT_texture_filter_anisotropic
Initializing GLX extensions
...using GLX_SGI_swap_control
...using GLX_SGI_video_sync
XF86 Gamma extension initialized

PIXELFORMAT: color(24-bits) Z(24-bit) stencil(0-bits)
MODE: 6, 1024 x 768 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_LINEAR
picmip: 0
texture bits: 0
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: enabled
anisotropy: 1.0
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----

------- sound initialization -------
/dev/dsp: No such file or directory
Could not open /dev/dsp
------------------------------------
Sound memory manager started
Sys_LoadDll(/home/owner/.etwolf/etmain/ui.mp.i386.so)... 
Sys_LoadDll(/home/owner/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/owner/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xac764f40  
Sys_LoadDll(ui) succeeded!
^3WARNING: Couldn't find image for shader ui/assets/icon_jaymod
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: owner-desktop
IP: 127.0.1.1
Started tty console (use +set ttycon 0 to disable)
Resolving etmaster.idsoftware.com
etmaster.idsoftware.com resolved to 192.246.40.60:27951
----- CL



i have deleted the gl stuff about the video cause it works
but the sound says no such file 
maybe this is the problem?

---

### Post by jechill on 2011-09-15
i have 11.04 and im trying to get wolfet to have sound
the game runs great good graphics i can connect to server everything is fine but no sound
ive tried everything posted still nothing
------- sound initialization -------
[COLOR="Red"]/dev/dsp: No such file or directory
Could not open /dev/dsp[/COLOR]
------------------------------------
Sound memory manager started
Sys_LoadDll(/home/owner/.etwolf/etmain/ui.mp.i386.so)... 
Sys_LoadDll(/home/owner/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/owner/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xac68bf40  
Sys_LoadDll(ui) succeeded!
^3WARNING: Couldn't find image for shader ui/assets/icon_jaymod
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: owner-desktop
IP: 127.0.1.1
Started tty console (use +set ttycon 0 to disable)
Resolving etmaster.idsoftware.com
etmaster.idsoftware.com resolved to 192.246.40.60:27951
RE_Shutdown( 1 )
Hunk_Clear: reset the hunk ok
----- Initializing Renderer ----
-------------------------------
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 6: 1024 768
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 1024x768
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: GeForce 7025 / nForce 630a/PCI/SSE2/3DNOW!
Initializing OpenGL extensions
...using GL_S3_s3tc
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...ignoring GL_NV_fog_distance
...ignoring GL_EXT_texture_filter_anisotropic
Initializing GLX extensions
...using GLX_SGI_swap_control
...using GLX_SGI_video_sync
XF86 Gamma extension initialized


PIXELFORMAT: color(24-bits) Z(24-bit) stencil(0-bits)
MODE: 6, 1024 x 768 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_LINEAR
picmip: 0
texture bits: 0
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: enabled
anisotropy: 1.0
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----
Sys_LoadDll(/home/owner/.etwolf/etmain/ui.mp.i386.so)... 
Sys_LoadDll(/home/owner/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/owner/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xac68bf40  
Sys_LoadDll(ui) succeeded!
^3WARNING: Couldn't find image for shader ui/assets/icon_jaymod
Resolving etmaster.idsoftware.com
etmaster.idsoftware.com resolved to 192.246.40.60:27951
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Shutdown tty console
owner@owner-desktop:~$ et
ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/owner/.etwolf/etmain/~~~~~~~~~~funboymenu9A.pk3 (6 files)
/home/owner/.etwolf/etmain/SuperGoldrush_Final.pk3 (170 files)
/home/owner/.etwolf/etmain/caen2.pk3 (85 files)
/home/owner/.etwolf/etmain/baserace_desert.pk3 (154 files)
/home/owner/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

----------------------
4178 files in pk3 files
execing default.cfg
couldn't exec language.cfg
execing profiles/Chill/etconfig.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 6: 1024 768
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 1024x768
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: GeForce 7025 / nForce 630a/PCI/SSE2/3DNOW!
Initializing OpenGL extensions
...using GL_S3_s3tc
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...ignoring GL_NV_fog_distance
...ignoring GL_EXT_texture_filter_anisotropic
Initializing GLX extensions
...using GLX_SGI_swap_control
...using GLX_SGI_video_sync
XF86 Gamma extension initialized


PIXELFORMAT: color(24-bits) Z(24-bit) stencil(0-bits)
MODE: 6, 1024 x 768 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_LINEAR
picmip: 0
texture bits: 0
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: enabled
anisotropy: 1.0
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----

------- sound initialization -------
/dev/dsp: No such file or directory
Could not open /dev/dsp
------------------------------------
Sound memory manager started
Sys_LoadDll(/home/owner/.etwolf/etmain/ui.mp.i386.so)... 
Sys_LoadDll(/home/owner/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/owner/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xac807f40  
Sys_LoadDll(ui) succeeded!
^3WARNING: Couldn't find image for shader ui/assets/icon_jaymod
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: owner-desktop
IP: 127.0.1.1
Started tty console (use +set ttycon 0 to disable)
Resolving etmaster.idsoftware.com
etmaster.idsoftware.com resolved to 192.246.40.60:27951
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Shutdown tty console
owner@owner-desktop:~$ sudo wget -q -O - [http://nullkey.kapsi.fi/et-sdl-sound/et-sdl-sound.gz](http://nullkey.kapsi.fi/et-sdl-sound/et-sdl-sound.gz) | gzip -d > et-sdl-sound && chmod a+x et-sdl-sound
[sudo] password for owner: 
owner@owner-desktop:~$ /et-sdl-sound
bash: /et-sdl-sound: No such file or directory
owner@owner-desktop:~$ et
ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/owner/.etwolf/etmain/~~~~~~~~~~funboymenu9A.pk3 (6 files)
/home/owner/.etwolf/etmain/SuperGoldrush_Final.pk3 (170 files)
/home/owner/.etwolf/etmain/caen2.pk3 (85 files)
/home/owner/.etwolf/etmain/baserace_desert.pk3 (154 files)
/home/owner/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

----------------------
4178 files in pk3 files
execing default.cfg
couldn't exec language.cfg
execing profiles/Chill/etconfig.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 6: 1024 768
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 1024x768
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: GeForce 7025 / nForce 630a/PCI/SSE2/3DNOW!
Initializing OpenGL extensions
...using GL_S3_s3tc
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...ignoring GL_NV_fog_distance
...ignoring GL_EXT_texture_filter_anisotropic
Initializing GLX extensions
...using GLX_SGI_swap_control
...using GLX_SGI_video_sync
XF86 Gamma extension initialized

PIXELFORMAT: color(24-bits) Z(24-bit) stencil(0-bits)
MODE: 6, 1024 x 768 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_LINEAR
picmip: 0
texture bits: 0
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: enabled
anisotropy: 1.0
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----

------- sound initialization -------
/dev/dsp: No such file or directory
Could not open /dev/dsp
------------------------------------
Sound memory manager started
Sys_LoadDll(/home/owner/.etwolf/etmain/ui.mp.i386.so)... 
Sys_LoadDll(/home/owner/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/owner/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xac764f40  
Sys_LoadDll(ui) succeeded!
^3WARNING: Couldn't find image for shader ui/assets/icon_jaymod
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: owner-desktop
IP: 127.0.1.1
Started tty console (use +set ttycon 0 to disable)
Resolving etmaster.idsoftware.com
etmaster.idsoftware.com resolved to 192.246.40.60:27951
----- CL



i have deleted the gl stuff about the video cause it works
but the sound says no such file 
maybe this is the problem?

---

### Post by jechill on 2011-09-15
sorry for the multi post i clicked too many times

---

### Post by Quazze on 2011-10-03
I still don't have sound either. I have already tried everything I found on the internet, none of the solutions worked... :(

---

### Post by bgainey on 2011-10-16
I have currently used ET with sound and with out . Unfortunately the 11.04 doesn't have the packages to run OSS sound . As I have done this many times as explained in this link [http://bloc.eurion.net/archives/2009/no-sound-problem-with-wolfenstein-enemy-territory/](http://bloc.eurion.net/archives/2009/no-sound-problem-with-wolfenstein-enemy-territory/)

As it says you need this .
[B]Install the “oss-compat” package. -> System , Administration , Synaptic Package Manager in the search just type oss-compat either or in the Ubuntu Software Center.
[/B]
After installing that you will need to download the script listed in the site I gave . [wolfsp-sdl-sound.sh]("http://bloc.eurion.net/wp-content/uploads/2009/12/wolfsp-sdl-sound.sh")

Open the wolfsp with text editor and change the line for the dir for the installation . "/usr/local/games/enemy-territory" as explained in the site I gave .

Once you have changed the dir you need to save and close the .sh and right click and choose properties and change the .sh to a excitable file .

I hope this helps for users with 11.04

My name is DoubleDragon fyi :)

---

### Post by DustofDust on 2011-10-18
[http://www.playdeb.net/updates/ubuntu/11.10/?q=enemy+territory](http://www.playdeb.net/updates/ubuntu/11.10/?q=enemy+territory)

Available for Ubuntu: 10.04, 10.10, 11.04, 11.10 
playdeb is really nice to get the games

---

### Post by Quazze on 2011-10-19
> **bgainey said:**
> I have currently used ET with sound and with out . Unfortunately the 11.04 doesn't have the packages to run OSS sound . As I have done this many times as explained in this link [http://bloc.eurion.net/archives/2009/no-sound-problem-with-wolfenstein-enemy-territory/](http://bloc.eurion.net/archives/2009/no-sound-problem-with-wolfenstein-enemy-territory/)

As it says you need this .
[B]Install the “oss-compat” package. -> System , Administration , Synaptic Package Manager in the search just type oss-compat either or in the Ubuntu Software Center.
[/B]
After installing that you will need to download the script listed in the site I gave . [wolfsp-sdl-sound.sh]("http://bloc.eurion.net/wp-content/uploads/2009/12/wolfsp-sdl-sound.sh")

Open the wolfsp with text editor and change the line for the dir for the installation . "/usr/local/games/enemy-territory" as explained in the site I gave .

Once you have changed the dir you need to save and close the .sh and right click and choose properties and change the .sh to a excitable file .

I hope this helps for users with 11.04

My name is DoubleDragon fyi :)

does this work for enemy territory? Because when I run this I get the error:
"./wolfsp-sdl-sound: line 1582: ./wolfsp.x86: No such file or directory"
and so it just quits.

I would guess that "wolfsp.x86" is a wolfenstein file. But so i just made a copy of the et.x86 file and named it wolfsp.x86 and it ran fine, except... still no sound :(.
I'm getting desperate, i've tried so many solutions I found online, but none will work (which is weird, because I don't understand why they work for others but not for me)

---

### Post by Perfect Storm on 2011-10-19
I know this is for other games, but it might be something to look at: [http://ubuntuforums.org/showthread.php?t=1705760](http://ubuntuforums.org/showthread.php?t=1705760)

---

### Post by bgainey on 2011-10-19
I have ran the script on 10.04 , 10.10 , 11.04 and 11.10 . Yeah its supposed to work " for me that is " can you post the log information when executing the script . You know when the terminal opens there is command lines that explain what is going on during the execution . The best way to accomplish this is to when the game starts and there is no sound . Open console and hit the ~ key and type /condump name_file.txt

If the game is installed by user it would be located in the /usr/local/games/enemy-territory/etmain/

The script is supposed to be auto detect sound drivers etc.. Tho I don't know what the sound driver you are using but I am unable to explain detailed information about it . 

When installing ET from my experience is that you can't play ET as root sound will never work and when it is installed it has to be installed in root . But permissioned to be used by user or group . Sudo -i doesn't help in this matter . It also is difficult for me as well I can always install Ubuntu all versions but I end up with out permissions my self they don't change in properties even on Dual Boot from windows xp cause the partition is mounted . 

Anyways to stop jabbering the best thing to do is open Pulse Audio Sound Controller or the sound Crontroler and make sure your on the right channel I think its #2

---

### Post by bgainey on 2011-10-19
I just got a question being you are on Ubuntu how was it installed . Cause if it's dual booting like I do you would be required to have to proper sound drivers installed on the Windows OS . For me I am using AC97 made by Realtek and the system during install it checks the system for drivers from windows . If I am not mistaken the Ubuntu 11.04 comes with Pulse Audio and in applications there should be a controller . There is where every thing would be controlled . Tho it wouldn't list the sound drivers properties it will list a selection of optional outputs .

Yeah sorry for the back to back post . Unfortunately install ET on Ubuntu is a challenge for many . But from what I am experiencing it is a lot of work but in the end it is worth the effort and time .

---

### Post by DustofDust on 2011-10-23
with [http://www.playdeb.net/](http://www.playdeb.net/) it is a one click install and it includes punkbuster which is a necessary anti cheat tool and a must have for all servers to play

if someone wants to play seriously on ubuntu than playdeb repo is a must

---

