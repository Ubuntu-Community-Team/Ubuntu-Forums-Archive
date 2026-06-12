---
title: "quake wars won't install"
date: 2008-04-23
forum: Gaming &amp; Leisure
---

### Post by ELD on 2008-04-23
quake wars always says "file creation failed" with no actual error message, anyone know how i can fix? :(

---

### Post by Wobedraggled on 2008-04-23
Are you installing as root?

either place the game in your home directory or install as root.

---

### Post by Perfect Storm on 2008-04-23
We need a little more info than that. Can you post step by step what you do, and best with terminal in/output.

---

### Post by ELD on 2008-04-23
That is just the thing all i get from terminal is the installers error message:
(same as root too wont even do it when root :()

[http://i43.photobucket.com/albums/e397/clericvash/Screenshot-2.png](http://i43.photobucket.com/albums/e397/clericvash/Screenshot-2.png)

---

### Post by digimars on 2008-04-25
> **ELD said:**
> That is just the thing all i get from terminal is the installers error message:
(same as root too wont even do it when root :()

[http://i43.photobucket.com/albums/e397/clericvash/Screenshot-2.png](http://i43.photobucket.com/albums/e397/clericvash/Screenshot-2.png)

The only way that I have been able to get this game installed was to restart into the "recovery mode" which is just root at a full terminal and install the game to the default locations.  It wouldn't install if I tried to install to a different directory.

---

### Post by kr00lplatinum on 2008-04-25
I was able to get Quake Wars installed however, I can't launch it. Here is what I do.

------------------------------------------------------------

robert@robert-ubuntu:~$ cd /home/robert/Documents/etqw
robert@robert-ubuntu:~/Documents/etqw$ ./etqw
ETQW 1.4.12247.12247  linux-x86 Jan  4 2008 13:52:05
found interface lo - loopback
found interface eth0 - 192.168.0.159/255.255.255.0
CPU: AMD CPU with MMX & 3DNow! & SSE & SSE2 & SSE3
ETQW using generic code for SIMD processing
enabled Flush-To-Zero mode
------ Initializing File System ------
Loaded pk4 /home/robert/Documents/etqw/base/game000.pk4 with checksum 0x1eefa237
Loaded pk4 /home/robert/Documents/etqw/base/game002.pk4 with checksum 0x5f707685
Loaded pk4 /home/robert/Documents/etqw/base/pak000.pk4 with checksum 0x442eb08b
Loaded pk4 /home/robert/Documents/etqw/base/pak001.pk4 with checksum 0x10e16e6
Loaded pk4 /home/robert/Documents/etqw/base/pak002.pk4 with checksum 0x8dbe7353
Loaded pk4 /home/robert/Documents/etqw/base/pak003.pk4 with checksum 0x99dfcabb
Loaded pk4 /home/robert/Documents/etqw/base/pak004.pk4 with checksum 0x7e49f838
Loaded pk4 /home/robert/Documents/etqw/base/pak005.pk4 with checksum 0x5ccc7213
Loaded pk4 /home/robert/Documents/etqw/base/pak006.pk4 with checksum 0x9edf1b7d
Loaded pk4 /home/robert/Documents/etqw/base/pak007.pk4 with checksum 0x74a1a2f
Loaded pk4 /home/robert/Documents/etqw/base/zpak_english000.pk4 with checksum 0x977c7bd0
Loaded pk4 /home/robert/Documents/etqw/base/zpak_english001.pk4 with checksum 0x6583cd8
Loaded pk4 /home/robert/Documents/etqw/base/zpak_english002.pk4 with checksum 0x8dc70e3d
Loaded pk4 /home/robert/Documents/etqw/base/zpak_french001.pk4 with checksum 0x3bd7a062
Loaded pk4 /home/robert/Documents/etqw/base/zpak_french002.pk4 with checksum 0x79287190
Loaded pk4 /home/robert/Documents/etqw/base/zpak_german001.pk4 with checksum 0xa694c3f1
Loaded pk4 /home/robert/Documents/etqw/base/zpak_german002.pk4 with checksum 0x64bee731
Loaded pk4 /home/robert/Documents/etqw/base/zpak_korean000.pk4 with checksum 0xd42c084
Loaded pk4 /home/robert/Documents/etqw/base/zpak_korean001.pk4 with checksum 0x4de6a4e7
Loaded pk4 /home/robert/Documents/etqw/base/zpak_korean002.pk4 with checksum 0x15d2c9af
Loaded pk4 /home/robert/Documents/etqw/base/zpak_polish001.pk4 with checksum 0x2575ff8e
Loaded pk4 /home/robert/Documents/etqw/base/zpak_polish002.pk4 with checksum 0x3ab92dd6
Loaded pk4 /home/robert/Documents/etqw/base/zpak_russian001.pk4 with checksum 0xf3e91581
Loaded pk4 /home/robert/Documents/etqw/base/zpak_russian002.pk4 with checksum 0x38b1a37c
Loaded pk4 /home/robert/Documents/etqw/base/zpak_spanish001.pk4 with checksum 0xd609566c
Loaded pk4 /home/robert/Documents/etqw/base/zpak_spanish002.pk4 with checksum 0xcf994ada
Current search path:
/home/robert/.etqwcl/base
/home/robert/Documents/etqw/base
/home/robert/Documents/etqw/base/zpak_spanish002.pk4 (119 files)
/home/robert/Documents/etqw/base/zpak_spanish001.pk4 (13 files)
/home/robert/Documents/etqw/base/zpak_russian002.pk4 (119 files)
/home/robert/Documents/etqw/base/zpak_russian001.pk4 (13 files)
/home/robert/Documents/etqw/base/zpak_polish002.pk4 (119 files)
/home/robert/Documents/etqw/base/zpak_polish001.pk4 (13 files)
/home/robert/Documents/etqw/base/zpak_korean002.pk4 (12 files)
/home/robert/Documents/etqw/base/zpak_korean001.pk4 (12 files)
/home/robert/Documents/etqw/base/zpak_korean000.pk4 (6 files)
/home/robert/Documents/etqw/base/zpak_german002.pk4 (119 files)
/home/robert/Documents/etqw/base/zpak_german001.pk4 (13 files)
/home/robert/Documents/etqw/base/zpak_french002.pk4 (119 files)
/home/robert/Documents/etqw/base/zpak_french001.pk4 (13 files)
/home/robert/Documents/etqw/base/zpak_english002.pk4 (117 files)
/home/robert/Documents/etqw/base/zpak_english001.pk4 (9 files)
/home/robert/Documents/etqw/base/zpak_english000.pk4 (1018 files)
/home/robert/Documents/etqw/base/pak007.pk4 (1510 files)
/home/robert/Documents/etqw/base/pak006.pk4 (3 files)
/home/robert/Documents/etqw/base/pak005.pk4 (2172 files)
/home/robert/Documents/etqw/base/pak004.pk4 (72 files)
/home/robert/Documents/etqw/base/pak003.pk4 (1133 files)
/home/robert/Documents/etqw/base/pak002.pk4 (1637 files)
/home/robert/Documents/etqw/base/pak001.pk4 (1067 files)
/home/robert/Documents/etqw/base/pak000.pk4 (9350 files)
/home/robert/Documents/etqw/base/game002.pk4 (3 files)
/home/robert/Documents/etqw/base/game000.pk4 (3 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
--------------------------------------
----- Initializing Decls -----
Decompressing the global token cache...3560Kb
------------------------------
couldn't exec 'etqwconfig.cfg'
execing 'localization/english/defaultbinds.cfg'
couldn't exec 'etqwbinds.cfg'
couldn't exec 'autoexec.cfg'
Vendor: Device:
/proc/cpuinfo CPU frequency: 2812.99 MHz
parse /proc/cpuinfo for CPU information
2 logical, 1 physical CPU(s)
detecting video ram (set sys_videoRam on command line to override) ..
trying /proc/dri/0/umm
guess failed, return default low-end VRAM setting ( 128MB VRAM )
Detected
 	1 2.81 GHz CPU
	2032 MB of System memory
	128 MB of Video memory on an optimal video architecture

This system qualifies for Low quality.
Initializing SDL subsystem
Loading GL driver 'libGL.so.1' through SDL
Desktop resolution: 1920x1200
execing 'specs/minspec.dat'
execing 'specs/minspec_cpu.dat'
execing 'specs/minspec_gamedetail.dat'
execing 'specs/minspec_gpu.dat'
execing 'specs/minspec_gpudetail.dat'
execing 'specs/minspec_lighting.dat'
execing 'specs/minspec_foliage.dat'
Vendor: Device:
execing 'specs/minspec_foliage.dat'
thread priority set to 1
Opening IP socket: localhost:-1
Failed to open server license code file for reading.
SDL_ListModes:
1920x1200 1680x1050 1440x900 1400x1050 1280x1024 1024x768 800x600 720x400 640x480 
SDL_ListModes are currently ignored for resolution filtering. Set r_useSDLModes to 1 if you want it
WARNING: SDL_SetVideoMode failed: Couldn't find matching GLX visual
------- Initializing renderSystem --------
----- R_InitOpenGL -----
signal caught: 'Segmentation fault', si_code 1
callstack:
0x0
[0x082e7e71]
[0x082e523d]
[0xb7faf440]
Trying to exit gracefully..
--------------- BSE Shutdown ----------------
---------------------------------------------
Shutting down SDL subsystem
idRenderSystem::Shutdown()
robert@robert-ubuntu:~/Documents/etqw$ 


Anyone got any ideas?

---

### Post by Natanael on 2008-04-26
I've got the same problem. Try to reinstall (uninstall, restart system, and install again) restricted drivers for you graphic card (System>Administration>Drivers).

---

### Post by Curlydave on 2008-04-26
I have another problem with Quake Wars. I had it working in Linux before, but I just did a clean install of Hardy, and am unable to successfully launch the game. It will go through some of the loading screens and appear to work, but instead of going into the main menu, it exits to a small, low-resolution view of the top left of the desktop. The keyboard works, and I can alt-tab to different windows, and interact with them using the keyboard. It appears that QW is no longer running. The mouse is completely dead. This requires a hard reboot. Any ideas?

---

### Post by ELD on 2008-04-26
I am pretty sure it's a dvd drive issue for me, tried to install without copying files from dvd and worked, think my dvd drive is on the blink..

---

### Post by Perfect Storm on 2008-04-26
> **Curlydave said:**
> I have another problem with Quake Wars. I had it working in Linux before, but I just did a clean install of Hardy, and am unable to successfully launch the game. It will go through some of the loading screens and appear to work, but instead of going into the main menu, it exits to a small, low-resolution view of the top left of the desktop. The keyboard works, and I can alt-tab to different windows, and interact with them using the keyboard. It appears that QW is no longer running. The mouse is completely dead. This requires a hard reboot. Any ideas?

See if it helps by disable compiz.

---

### Post by Sleaka J on 2008-04-27
Wow, guess I'm lucky. The biggest problem I've got with Quake Wars is that my screensaver kicks in while I'm playing.

Does anybody know of a way to leave the screensaver turned on and still be able to play?

---

### Post by Curlydave on 2008-04-27
> **Artificial Intelligence said:**
> See if it helps by disable compiz.

Is there anything required to do this besides turning off desktop effects in Compiz? I tried it, and it still broke on launch. I remember in the past, it would cause performance problems in-game, but never caused the game to fail to load a reboot-requiring problem like this.

---

### Post by slambrick on 2008-05-21
> **ELD said:**
> quake wars always says "file creation failed" with no actual error message, anyone know how i can fix? :(
I have exactly the same issue. Was it resolved? please tell me how to fix it.

---

### Post by ELD on 2008-05-21
> **slambrick said:**
> I have exactly the same issue. Was it resolved? please tell me how to fix it.

Mine is a dodgey dvd drive, i need a new one.

---

### Post by jaygo on 2008-08-21
@Sleaka
look for options to disable screensavers when full-screen apps are running

@file creation failed
the issue for me was that I ran out of disk space on my root (/ ) partition, where I was installing it. Copying the 4 GB of files from the DVD was failing and thus the installation choked. Hope that helps someone.

GLHF

---

