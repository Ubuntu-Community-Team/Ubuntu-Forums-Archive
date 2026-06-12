---
title: "Problem with mupen64plus"
date: 2016-07-15
forum: Emulators
---

### Post by cranerja on 2016-07-15
Hello,

I was trying to launch a game via mupen64plus but it crashes:

```
$ mupen64plus /hdd/EmulatedGames/64/zeldamajorasmask.z64 __  __                         __   _  _   ____  _             
|  \/  |_   _ _ __   ___ _ __  / /_ | || | |  _ \| |_   _ ___ 
| |\/| | | | | '_ \ / _ \ '_ \| '_ \| || |_| |_) | | | | / __|  
| |  | | |_| | |_) |  __/ | | | (_) |__   _|  __/| | |_| \__ \  
|_|  |_|\__,_| .__/ \___|_| |_|\___/   |_| |_|   |_|\__,_|___/  
             |_|         http://code.google.com/p/mupen64plus/  
Mupen64Plus Console User-Interface Version 2.5.0


UI-Console: attached to core library 'Mupen64Plus Core' version 2.5.0
UI-Console:             Includes support for Dynamic Recompiler.
UI-Console:             Includes support for MIPS r4300 Debugger.
Core: Goodname: Legend of Zelda, The - Majora's Mask (U) [!]
Core: Name: ZELDA MAJORA'S MASK 
Core: MD5: 2A0A8ACB61538235BC1094D297FB6556
Core: CRC: 5354631C 3A2DEF0
Core: Imagetype: .z64 (native)
Core: Rom size: 33554432 bytes (or 32 Mb or 256 Megabits)
Core: Version: 144B
Core: Manufacturer: Nintendo
Core: Country: USA
UI-Console Status: Cheat codes disabled.
UI-Console: using Video plugin: 'Mupen64Plus OpenGL Video Plugin by Rice' v2.5.0
UI-Console: using Audio plugin: 'Mupen64Plus SDL Audio Plugin' v2.5.0
UI-Console: using Input plugin: 'Mupen64Plus SDL Input Plugin' v2.5.0
UI-Console: using RSP plugin: 'Hacktarux/Azimer High-Level Emulation RSP Plugin' v2.5.0
Input: 1 SDL joysticks were found.
Input: N64 Controller #1: Using auto-config with SDL joystick 0 ('Microsoft X-Box 360 pad')
Input: 1 controller(s) found, 1 plugged in and usable in the emulator
Input Warning: Couldn't open rumble support for joystick #1
Input Warning: Couldn't open rumble support for joystick #2
Input Warning: Couldn't open rumble support for joystick #3
Input Warning: Couldn't open rumble support for joystick #4
Input: Mupen64Plus SDL Input Plugin version 2.5.0 initialized.
Video: SSE processing enabled.
Video: Found ROM 'ZELDA MAJORA'S MASK', CRC 1c635453f0dea203-45
Video: Enabled hacks for game: 'ZELDA MAJORA'S MASK'
Video: Initializing OpenGL Device Context.
Core: Setting 32-bit video mode: 1920x1080
Video Warning: Failed to set GL_SWAP_CONTROL to 0. (it's 24)
Video Warning: Failed to set GL_BUFFER_SIZE to 32. (it's 24)
Video Warning: Failed to set GL_DEPTH_SIZE to 16. (it's 24)
Video: Using OpenGL: Intel Open Source Technology Center - Mesa DRI Intel(R) HD Graphics 5600 (Broadwell GT2)  : 3.0 Mesa 11.2.0
Audio: Initializing SDL audio subsystem...
Input Warning: Couldn't open rumble support for joystick #1
Input Warning: Couldn't open rumble support for joystick #2
Input Warning: Couldn't open rumble support for joystick #3
Input Warning: Couldn't open rumble support for joystick #4
Core: Starting R4300 emulator: Dynamic Recompiler
Core: R4300: starting 64-bit dynamic recompiler at: 0x7f3ad3a9b6e0
Core Error: VidExt_ResizeWindow() called in fullscreen mode.
Core Error: VidExt_ResizeWindow() called in fullscreen mode.
Video Error: Failed to set 32-bit video mode: 1920x1080
^CCore Status: Stopping emulation.
Core: R4300 emulator finished.
Core Status: Rom closed.

```

I tried a few things before getting it work in a window within m64py. The problem is that it does not work with the Settings->Graphics->Video Extension disabled, meaning full screen is not possible.

How can I run in full screen and from the terminal?

---

### Post by deadflowr on 2016-07-15
Move to Emulators

You might try changing video plugins.
Glide64 works for me for full screen.

In the mupen64plus.cfg file in the section marked 
[UI-console]
simply change the Video-Plugin =
from mupen64plus-video-rice
to mupen64plus-video-glide64

See if that makes any difference.

Also see how well it performs.

I find changing plugins to be rather hit or miss.

If it misses then simply change it back to the rice plugin.

Or maybe see about any others.
Available plugins are stored in /use/lib/x86_64-gnu-linux/mupen64plus
simply use the name without the.so extension.

I'm not sure how well it'll work.
But hope it does

---

### Post by cranerja on 2016-07-15
> **deadflowr said:**
> Move to Emulators

You might try changing video plugins.
Glide64 works for me for full screen.

In the mupen64plus.cfg file in the section marked 
[UI-console]
simply change the Video-Plugin =
from mupen64plus-video-rice
to mupen64plus-video-glide64

See if that makes any difference.

Also see how well it performs.

I find changing plugins to be rather hit or miss.

If it misses then simply change it back to the rice plugin.

Or maybe see about any others.
Available plugins are stored in /use/lib/x86_64-gnu-linux/mupen64plus
simply use the name without the.so extension.

I'm not sure how well it'll work.
But hope it does

I had success with glide64mk2! 

I was trying glide64mk which didn't work.

Thanks for the quick response!

---

