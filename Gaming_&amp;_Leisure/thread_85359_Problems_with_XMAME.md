---
title: "Problems with XMAME"
date: 2005-11-02
forum: Gaming &amp; Leisure
---

### Post by tigrez on 2005-11-02
I've installed the last version of xmame, but I've this error:

info: trying to parse: /etc/xmame/xmamerc
error: unknown option bpp, on line 15 of file: /etc/xmame/xmamerc
   ignoring line
error: unknown option scanlines, on line 21 of file: /etc/xmame/xmamerc
   ignoring line
error: unknown option artwork_resolution, on line 27 of file: /etc/xmame/xmamerc   ignoring line
error: unknown option sound, on line 59 of file: /etc/xmame/xmamerc
   ignoring line
Error: joytype 4 is not available
   ignoring line
error: unknown option joyusb-calibrate, on line 71 of file: /etc/xmame/xmamerc
   ignoring line
error: unknown option mouse, on line 72 of file: /etc/xmame/xmamerc
   ignoring line
error: unknown option history_file, on line 97 of file: /etc/xmame/xmamerc
   ignoring line
error: unknown option mameinfo_file, on line 98 of file: /etc/xmame/xmamerc
   ignoring line
error: unknown option crconly, on line 109 of file: /etc/xmame/xmamerc
   ignoring line
info: trying to parse: /root/.xmame/xmamerc
info: trying to parse: /etc/xmame/xmame-SDLrc
info: trying to parse: /root/.xmame/xmame-SDLrc
info: trying to parse: /etc/xmame/rc/polyplayrc
info: trying to parse: /root/.xmame/rc/polyplayrc
loading rom 0: cpu_0000.37
loading rom 1: cpu_0400.36
loading rom 2: cpu_0800.35
loading rom 3: 2_-_1000.14
loading rom 4: 2_-_1400.10
loading rom 5: 2_-_1800.6
loading rom 6: 2_-_1c00.2
loading rom 7: 2_-_2000.15
loading rom 8: 2_-_2400.11
loading rom 9: 2_-_2800.7
loading rom 10: 2_-_2c00.3
loading rom 11: 2_-_3000.16
loading rom 12: 2_-_3400.12
loading rom 13: 2_-_3800.8
loading rom 14: 2_-_3c00.4
loading rom 15: 2_-_4000.17
loading rom 16: 2_-_4400.13
loading rom 17: 2_-_4800.9
loading rom 18: 2_-_4c00.5
loading rom 19: 1_-_5000.30
loading rom 20: 1_-_5400.26
loading rom 21: 1_-_5800.22
loading rom 22: 1_-_5c00.18
loading rom 23: 1_-_6000.31
loading rom 24: 1_-_6400.27
loading rom 25: 1_-_6800.23
loading rom 26: 1_-_6c00.19
loading rom 27: 1_-_7000.32
loading rom 28: 1_-_7400.28
loading rom 29: 1_-_7800.24
loading rom 30: 1_-_7c00.20
loading rom 31: 1_-_8000.33
loading rom 32: 1_-_8400.29
loading rom 33: 1_-_8800.25
loading rom 34: 1_-_8c00.21
loading rom 35: char.1
done
cpu_0000.37  NOT FOUND
cpu_0400.36  NOT FOUND
cpu_0800.35  NOT FOUND
2_-_1000.14  NOT FOUND
2_-_1400.10  NOT FOUND
2_-_1800.6   NOT FOUND
2_-_1c00.2   NOT FOUND
2_-_2000.15  NOT FOUND
2_-_2400.11  NOT FOUND
2_-_2800.7   NOT FOUND
2_-_2c00.3   NOT FOUND
2_-_3000.16  NOT FOUND
2_-_3400.12  NOT FOUND
2_-_3800.8   NOT FOUND
2_-_3c00.4   NOT FOUND
2_-_4000.17  NOT FOUND
2_-_4400.13  NOT FOUND
2_-_4800.9   NOT FOUND
2_-_4c00.5   NOT FOUND
1_-_5000.30  NOT FOUND
1_-_5400.26  NOT FOUND
1_-_5800.22  NOT FOUND
1_-_5c00.18  NOT FOUND
1_-_6000.31  NOT FOUND
1_-_6400.27  NOT FOUND
1_-_6800.23  NOT FOUND
1_-_6c00.19  NOT FOUND
1_-_7000.32  NOT FOUND
1_-_7400.28  NOT FOUND
1_-_7800.24  NOT FOUND
1_-_7c00.20  NOT FOUND
1_-_8000.33  NOT FOUND
1_-_8400.29  NOT FOUND
1_-_8800.25  NOT FOUND
1_-_8c00.21  NOT FOUND
char.1       NOT FOUND
ERROR: required files are missing, the game cannot be run.

:(

---

### Post by leech on 2005-11-02
Is that the version of xmame that is in Breezy?  Or one you compiled yourself?

Looks to me like it just can't find the rom you're trying to play.  Just do 'xmame -rompath <path where the rom is>' and you should be good.  For example, if I wanted to play pacman ```
xmame -rompath /usr/share/games/xmame/roms/pacman.zip
```

Leech

---

### Post by tigrez on 2005-11-03
I'm using a newer version, 0.101, i've installed the RPM via alien. 
If I remove all xmame package and reinstall che Ubuntu xmame, I give the same errors. 
Your solution don't work, it give me the same problem. 
Maybe a zlib or permission problem?

---

### Post by tigrez on 2005-11-03
Ok, I've removed all x-mame related stuff, and reinstalled only xmame.sdl 0.86 (ubunutu version) , now it work...
But the problem now is GXMame... 
Anyway thanks!

---

### Post by leech on 2005-11-04
yeah, I noticed a problem with the permissions as well.  But then I copied all my mame roms over to my linux drive from an NTFS drive, so the permissions were set differently.  

What is gxmame doing?  Or not doing as the case may be.

Leech

---

### Post by BoyOfDestiny on 2005-11-04
[QUOTE=tigrez]Ok, I've removed all x-mame related stuff, and reinstalled only xmame.sdl 0.86 (ubunutu version) , now it work...
But the problem now is GXMame... 
Anyway thanks![/QUOTE]

I need to build the latest versions... 

[http://www.safaribans.com/gpl/](http://www.safaribans.com/gpl/)

These have the sources and debs to emulators (and some music players) I've compiled under breezy.

Try advancemenu instead of gxmame. Make sure to install advancemame first, so then advancemenu will detect it automagically.

I will let you guys know when I update them. New versions of mednafen, zsnes (cvs that is), advmame, advmenu, etc...

I need ebuilds... jk

---

