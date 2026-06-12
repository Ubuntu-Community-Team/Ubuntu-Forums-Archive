---
title: "Hmmm XQF &amp; Enemy Territory"
date: 2007-10-25
forum: Gaming &amp; Leisure
---

### Post by 2sugars on 2007-10-25
I have been using Ubuntu for about a week now... :)

It started like this...

ET installed fine could load up game and play etc. Decided to install XQF to just speed connecting up. Installed XQF and connected to server whereupon it jumps back to desktop! Run XQF from console and get openGL error.

Search ubuntu find various posts on 3d drivers etc, so install envy and  let it do it stuff. Restarted and still same problem. Cannot even load et  off its own file.

One other thing, before envy if i disabled the options set_fs game on connect and the pb one i could load et up but as loading bar reached end it would jump back to desktop.

Here is what the console spits up 

[COLOR="Blue"]debug(1) 13:05:50 game.c:2356 q3_exec() - Check for '/home/richard/etproto84' as a command
debug(1) 13:05:50 game.c:2445 q3_exec() - Got 1 for punkbuster

debug(1) 13:05:50 game.c:3384 get_custom_arguments() - get_custom_arguments: Didn't find an entry for etpro
debug(1) 13:05:50 game.c:2528 q3_exec() - argument count 10
debug(0) 13:05:50 launch.c:238 client_launch_exec() - /home/richard/et # +set # r_gldriver # libGL.so.1 # +connect # 82.192.80.137:27920 # +exec # daddy.cfg # +exec # daddy.cfg
ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/richard/.etwolf/etmain/sw_oasis_b3.pk3 (45 files)
/home/richard/.etwolf/etmain/RTCcampaign2.pk3 (1 files)
/home/richard/.etwolf/etmain/reactor_final.pk3 (115 files)
/home/richard/.etwolf/etmain/gwadv04.pk3 (2 files)
/home/richard/.etwolf/etmain/et_village.pk3 (58 files)
/home/richard/.etwolf/etmain/etmapcycle.pk3 (3 files)
/home/richard/.etwolf/etmain/camp_imp.pk3 (2 files)
/home/richard/.etwolf/etmain/bremen_b2.pk3 (82 files)
/home/richard/.etwolf/etmain/braundorf_b4.pk3 (51 files)
/home/richard/.etwolf/etmain/adlernest.pk3 (113 files)
/home/richard/.etwolf/etmain/13th.pk3 (1 files)
/home/richard/.etwolf/etmain
/home/richard/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/home/richard/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/home/richard/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/home/richard/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/home/richard/usr/local/games/enemy-territory/etmain

----------------------
4236 files in pk3 files
execing default.cfg
couldn't exec language.cfg
execing profiles/tboy/etconfig.cfg
com_zoneMegs will be changed upon restarting.
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
Couldn't get a visual
...WARNING: could not set the given mode (6)
Initializing OpenGL display
...setting mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 640x480
Couldn't get a visual
...WARNING: could not set the given mode (3)
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Sys_Error: GLimp_Init() - could not load OpenGL subsystem[/COLOR]

Here is what lspci | grep -i nvidia says
[COLOR="Blue"]
00:00.0 Host bridge: nVidia Corporation nForce3 250Gb Host Bridge (rev a1)
00:01.0 ISA bridge: nVidia Corporation nForce3 250Gb LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation nForce 250Gb PCI System Management (rev a1)
00:02.0 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.2 USB Controller: nVidia Corporation nForce3 EHCI USB 2.0 Controller (rev a2)
00:08.0 IDE interface: nVidia Corporation CK8S Parallel ATA Controller (v2.5) (rev a2)
00:09.0 IDE interface: nVidia Corporation CK8S Serial ATA Controller (v2.5) (rev a2)
00:0a.0 IDE interface: nVidia Corporation CK8S Serial ATA Controller (v2.5) (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 250Gb AGP Host to PCI Bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation nForce3 250Gb PCI-to-PCI Bridge (rev a2)
01:00.0 VGA compatible controller: nVidia Corporation NV40 [GeForce 6800] (rev a1)[/COLOR]


I have an Nvidia Geforce 6800. Can anyone point me in right direction?

 May need ABC instructions :)

---

