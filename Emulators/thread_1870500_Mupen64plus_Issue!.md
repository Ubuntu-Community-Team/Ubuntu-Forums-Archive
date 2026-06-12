---
title: "Mupen64plus Issue!"
date: 2011-10-27
forum: Emulators
---

### Post by owenc on 2011-10-27
Hey all! Recently upgraded to 11.10 after a huge farce trying to dual-boot Windows and Ubuntu (in which I eventually blatted Windows off the computer and gave Ubuntu sole ownership of my hard-drive).

Around 2 days in I opened up mupen64plus for the first time since upgrading. It opens up fine but when I got to open a rom nothing happens and everything just closes.

I decided to open up mupen on terminal instead to try and see what it says about the error. I recieved the following:

> owenc@owenc-laptop:~$ mupen64plus
 __  __                         __   _  _   ____  _             
|  \/  |_   _ _ __   ___ _ __  / /_ | || | |  _ \| |_   _ ___ 
| |\/| | | | | '_ \ / _ \ '_ \| '_ \| || |_| |_) | | | | / __|  
| |  | | |_| | |_) |  __/ | | | (_) |__   _|  __/| | |_| \__ \  
|_|  |_|\__,_| .__/ \___|_| |_|\___/   |_| |_|   |_|\__,_|___/  
             |_|         [http://code.google.com/p/mupen64plus/](http://code.google.com/p/mupen64plus/)  
Version 1.5

Config Dir:  /home/owenc/.config/mupen64plus/
Data Dir:  /home/owenc/.local/share/mupen64plus/
Cache Dir:  /home/owenc/.cache/mupen64plus/
Install Dir: /usr/share/mupen64plus/
Plugin Dir:  /usr/lib/mupen64plus/

Rescanning rom cache.
Rom cache up to date. 0 ROMs.
Compression: Uncompressed
Imagetype: .z64 (native)
Rom size: 41943040 bytes (or 40 Mb or 320 Megabits)
MD5: A722F8161FF489943191330BF8416496
80 37 12 40
ClockRate = f
Version: 144b
CRC: 65eee53a ed7d733c
Name: PAPER MARIO
Manufacturer: Nintendo
Cartridge_ID: 514d
Country: USA
PC = 80125c00
EEPROM type: 0
init timer!
[blight's SDL input plugin]: version 0.0.10 initialized.
memory initialized
fb_clear 0 fb_smart 1
extensions 'CHROMARANGE TEXCHROMA TEXMIRROR PALETTE6666 FOGCOORD EVOODOO TEXTUREBUFFER TEXFMT'
fb_hires
(II) Initializing SDL video subsystem...
(II) Getting video info...
(II) Setting video mode 640x480...
The program 'mupen64plus' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadRequest (invalid request code or no such operation)'.
  (Details: serial 14 error_code 1 request_code 138 minor_code 66)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

I haven't a clue what any of this means at all so if you any of you could enlighten me and help me get to the bottom of this I'd be so grateful!

EDIT: just found out I have the exact same issue with cheese:(!

---

