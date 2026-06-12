---
title: "Mupen64plus errors :/"
date: 2016-01-11
forum: Emulators
---

### Post by awesomeant04 on 2016-01-11
So I'm attempting to run a few Nintendo 64 roms with mupen64plus, CLI version and I get a constant error, and haven't found a workaround after searching the web for hours. The terminal output: 

[HR][/HR]|  \/  |_   _ _ __   ___ _ __  / /_ | || | |  _ \| |_   _ ___ 
| |\/| | | | | '_ \ / _ \ '_ \| '_ \| || |_| |_) | | | | / __|  
| |  | | |_| | |_) |  __/ | | | (_) |__   _|  __/| | |_| \__ \  
|_|  |_|\__,_| .__/ \___|_| |_|\___/   |_| |_|   |_|\__,_|___/  
             |_|         [http://code.google.com/p/mupen64plus/](http://code.google.com/p/mupen64plus/)  
Mupen64Plus Console User-Interface Version 2.5.0


UI-Console: attached to core library 'Mupen64Plus Core' version 2.5.0
UI-Console:             Includes support for Dynamic Recompiler.
UI-Console:             Includes support for MIPS r4300 Debugger.
Core: Goodname: Mortal Kombat 4 (U) [!]
Core: Name: MORTAL KOMBAT 4     
Core: MD5: C70B91430866300CE38B49098019EF9D
Core: CRC: 417DD4F4 1B482FE2
Core: Imagetype: .v64 (byteswapped)
Core: Rom size: 16777216 bytes (or 16 Mb or 128 Megabits)
Core: Version: 1449
Core: Manufacturer: Nintendo
Core: Country: USA
UI-Console Status: Cheat codes disabled.
Video Warning: Old parameter config version detected : 0, updating to 1;
UI-Console: using Video plugin: 'Mupen64Plus OpenGL Video Plugin by Rice' v2.5.0
UI-Console: using Audio plugin: 'Mupen64Plus SDL Audio Plugin' v2.5.0
UI-Console: using Input plugin: 'Mupen64Plus SDL Input Plugin' v2.5.0
UI-Console: using RSP plugin: 'Hacktarux/Azimer High-Level Emulation RSP Plugin' v2.5.0
Video Warning: Old parameter config version detected : 0, updating to 1;
Input: 1 SDL joysticks were found.
Input: N64 Controller #1: Using manual config for SDL joystick 0
Input: 1 controller(s) found, 1 plugged in and usable in the emulator
Input: Rumble activated on N64 joystick #1
Input Warning: Couldn't open rumble support for joystick #2
Input Warning: Couldn't open rumble support for joystick #3
Input Warning: Couldn't open rumble support for joystick #4
Input: Mupen64Plus SDL Input Plugin version 2.5.0 initialized.
Video: Disabled SSE processing.
Video: Found ROM 'MORTAL KOMBAT 4', CRC f4d47d41e22f481b-45
Video: Initializing OpenGL Device Context.
Core: Setting 16-bit video mode: 320x240
Core Error: SDL_SetVideoMode failed: Could not create GL context
Video Error: Failed to set 16-bit video mode: 320x240
Core Status: Rom closed.[HR][/HR]The input is:


[HR][/HR]mupen64plus ~/Roms/"Mortal Kombat 4 (USA).n64"
[HR][/HR]

---

### Post by MikeCyber on 2016-01-12
looks like you don't have the proprietary Nvidia etc. drivers installed or you miss something alike sdl_Videosomething.
Try:
ldd mupen64plug
that should show missing libs.

---

### Post by deadflowr on 2016-01-12
Moved to Emulators

I'm tempted to suggest trying a different video plugin.
Use the --gfx option or change the video plugin in the mupen64plus.cfg file.

Graphic card info might help figure out what is what, as well...

---

### Post by awesomeant04 on 2016-01-12
MikeCyber: "ldd mupen64plug" comes with the error "ldd: ./mupen64plug: No such file or directory" 
Also since I believe you made a spelling error, I've tried "ldd mupen64plus" as well and to the same result.

deadflowr: I forgot to mention that I've tinkered extensively with the video plugins. Also my video card is an intel gm945, I have a netbook. It worked perfectly fine a few months back, maybe the new updates removed support somehow.

---

