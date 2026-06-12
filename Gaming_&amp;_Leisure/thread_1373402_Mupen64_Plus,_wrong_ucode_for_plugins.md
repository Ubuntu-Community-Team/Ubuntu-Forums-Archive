---
title: "Mupen64 Plus, wrong ucode for plugins?"
date: 2010-01-05
forum: Gaming &amp; Leisure
---

### Post by Selvaard on 2010-01-05
I have already installed mupen64plus from Ubuntu's Software Center, and I downloaded the roms, but when it comes to execute the roms it give this problem (i'm trying to get mupen64 running ok instead of emulating proyect64 with wine):

rober@rober-laptop:~$ mupen64plus 
 __  __                         __   _  _   ____  _             
 |  \/  |_   _ _ __   ___ _ __  / /_ | || | |  _ \| |_   _ ___ 
 | |\/| | | | | '_ \ / _ \ '_ \| '_ \| || |_| |_) | | | | / __|  
 | |  | | |_| | |_) |  __/ | | | (_) |__   _|  __/| | |_| \__ \  
 |_ |  |_|\__,_| .__/ \___|_| |_|\___/   |_| |_|   |_|\__,_|___/  
             |_|         [http://code.google.com/p/mupen64plus/](http://code.google.com/p/mupen64plus/)  
Version 1.5


(mupen64plus:3134): Gtk-WARNING **: Theme directory  of theme Azenis Icons has no size field

Config Dir:  /home/rober/.config/mupen64plus/
Data Dir:  /home/rober/.local/share/mupen64plus/
Cache Dir:  /home/rober/.cache/mupen64plus/
Install Dir: /usr/share/mupen64plus/
Plugin Dir:  /usr/lib/mupen64plus/

Rescanning rom cache.
Scanning... /home/rober/Documentos/Roms/
Rom cache up to date. 3 ROMs.
Compression: Zip
Imagetype: .z64 (native)
Rom size: 33554432 bytes (or 32 Mb or 256 Megabits)
MD5: E040DE91A74B61E3201DB0E2323F768A
80 37 12 40
ClockRate = f
Version: 1449
CRC: b044b569 373c1985
Name: THE LEGEND OF ZELDA
Manufacturer: Nintendo
Cartridge_ID: 4c5a
Country: Europe (0x50)
PC = 80000400
EEPROM type: 0
init timer!
[RiceVideo] SSE processing enabled.
[blight's SDL input plugin]: Couldn't open device file '/dev/input/event5' for rumble support.
[blight's SDL input plugin]: version 0.0.10 initialized.
memory initialized
[RiceVideo] SSE processing enabled.
[RiceVideo] Enabled hacks for game: 'THE LEGEND OF ZELDA'
InitExternalTextures
Initializing OpenGL Device Context
(II) Initializing SDL video subsystem...
(II) Getting video info...
(II) Setting video mode 640x480...
Tungsten Graphics, Inc - Mesa DRI Mobile Intel® GM45 Express Chipset GEM 20090712 2009Q2 RC3 x86/MMX/SSE2 : 2.1 Mesa 7.6.1-rc3
Error: The core thread recieved a SIGSEGV signal.
This means it tried to access protected memory.
Maybe you have set a wrong ucode for one of the plugins!
SIGSEGV in core thread caught:
    errno = 0 (Éxito)
    address = 0x2D312E36
                address not mapped to object

I'm yet totally new to ubuntu, so I would be grateful if you could help me with some doubts..._How do I set a ''right'' ucode for one of the plugins? How do I know which is the plugin I have to correct? Where do I find this plugins? What is an ucode, and what is SIGSEGV?_
Thank you for your time, really :D

Ah, graphically, a black screen appears but it won't load the rom (ocarina of time btw)

---

### Post by manco on 2010-01-05
I don't really have an answer, but I am also downloaded Mupen64plus from the software center, and I can't get it working quite right either.

---

### Post by Rhemat on 2010-06-04
I'm having this problem too, and the last time I used the program, it worked.

---

### Post by rafe101 on 2010-10-27
I just installed Mupen64plus from synaptic and am also getting this error--well, sometimes. The other times I don't get a message but the roms never start. I just have a black screen.

Has anyone figured anything out about this? I have tried both the Rice and Glide plugins.

P.S.

I just thought of something important. I'm using the nouveau drivers. Maybe that is my problem. I really want to continue using them, but I wish the 3D support would catch up.

---

### Post by coldchris on 2010-10-30
it's all about the configuration of graphic settings. 
Just enter graphic settings from Options menu and change your Open Gl Depth Buffer to 16-Bit(Def). I got the same error message when i changed the depth Buffer to 32 bit.

---

### Post by rafe101 on 2010-11-01
That didn't work for me. I really think it's the driver I'm using.

---

