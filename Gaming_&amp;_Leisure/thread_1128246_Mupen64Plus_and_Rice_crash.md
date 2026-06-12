---
title: "Mupen64Plus and Rice crash"
date: 2009-04-17
forum: Gaming &amp; Leisure
---

### Post by GepettoBR on 2009-04-17
Rice's video plugin is the only one that supports hi-res textures in Mupen64Plus, and, owning a N64 that still works very well, hi-res textures are the only reason I'd want to play in an emulator at all. However, Rice is the only plugin that doesn't work for me. It crashes the emulator as soon as I try to launch a game.

Does anyone know how to fix this?

Here's the terminal output: ```
 __  __                         __   _  _   ____  _             
|  \/  |_   _ _ __   ___ _ __  / /_ | || | |  _ \| |_   _ ___ 
| |\/| | | | | '_ \ / _ \ '_ \| '_ \| || |_| |_) | | | | / __|  
| |  | | |_| | |_) |  __/ | | | (_) |__   _|  __/| | |_| \__ \  
|_|  |_|\__,_| .__/ \___|_| |_|\___/   |_| |_|   |_|\__,_|___/  
             |_|         http://code.google.com/p/mupen64plus/  
Version 1.5

/home/paulo/.themes/Dust/gtk-2.0/gtkrc:719: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/paulo/.themes/Dust/gtk-2.0/gtkrc:720: Murrine configuration option "lightborder_ratio" will be deprecated in future releases. Please use "lightborder_shade" instead.
Config Dir:  /home/paulo/.mupen64plus/
Install Dir: /usr/local/share/mupen64plus/
Plugin Dir:  /usr/local/share/mupen64plus/plugins/

Rescanning rom cache.
Scanning... /data/Games/ROMS-Emulation/N64/N64-ROMs/Extracted/
Rom cache up to date. 140 ROMs.
Compression: Uncompressed
Imagetype: .z64 (native)
Rom size: 33554432 bytes (or 32 Mb or 256 Megabits)
MD5: 5BD1FE107BF8106B2AB6650ABECD54D6
80 37 12 40
ClockRate = f
Version: 1449
CRC: ec7011b7 7616d72b
Name: THE LEGEND OF ZELDA
Manufacturer: 43000000
Cartridge_ID: 4c5a
Country: USA
PC = 80000400
EEPROM type: 0
init timer!
[RiceVideo] SSE processing enabled.
[blight's SDL input plugin]: Couldn't open device file '/dev/input/event5' for rumble support.
[blight's SDL input plugin]: version 0.0.10 initialized.
init timer!
[RiceVideo] SSE processing enabled.
[blight's SDL input plugin]: Couldn't open device file '/dev/input/event5' for rumble support.
[blight's SDL input plugin]: version 0.0.10 initialized.
memory initialized
[RiceVideo] SSE processing enabled.
[RiceVideo] Found ROM 'THE LEGEND OF ZELDA', CRC b71170ec2bd71676-45
[RiceVideo] Enabled hacks for game: 'THE LEGEND OF ZELDA'
InitExternalTextures
Texture loading option is enabledFinding all hires texturesInitializing OpenGL Device Context
(II) Initializing SDL video subsystem...
(II) Getting video info...
(II) Setting video mode 800x600...
(EE) Error setting video mode 800x600: Couldn't find matching GLX visual
[RiceVideo] OpenGL Combiner: Nvidia
Error: The core thread recieved a SIGSEGV signal.
This means it tried to access protected memory.
Maybe you have set a wrong ucode for one of the plugins!
SIGSEGV in core thread caught:
	errno = 0 (Success)
	address = 0x00000000
                address not mapped to object
mupen64plus: ../../src/xcb_lock.c:33: _XCBUnlockDisplay: Assertion `xcb_get_request_sent(dpy->xcb->connection) == dpy->request' failed.
Aborted
```

I'm running 64-bit Intrepid, have a nVidia GeForce 8600GT with restricted drivers enabled and am using the latest Mupen64Plus build from the Google Code page.

---

### Post by wastvedt on 2009-06-02
Hi. I have the same issue, with 32-bit Jaunty. Did you ever get a fix for this?
-Trygve

---

### Post by GepettoBR on 2009-06-02
Running Mupen64Plus as root worked, but that's not really something we should do. I did other things, including a chown on the entire folder containing the emulator and plugins, but I don't remember if that solved it or not - I do know that after upgrading to Jaunty it's now working.

---

### Post by wastvedt on 2009-06-06
For anyone googling this, I can confirm that both running Mupen as root and, preferably, a chown on ~/.mupen64plus solved the problem. Thanks for the hint!

---

