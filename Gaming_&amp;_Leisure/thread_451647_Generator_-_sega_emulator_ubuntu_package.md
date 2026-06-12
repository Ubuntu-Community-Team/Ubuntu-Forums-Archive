---
title: "Generator - sega emulator ubuntu package"
date: 2007-05-22
forum: Gaming &amp; Leisure
---

### Post by megamaced on 2007-05-22
------------------------------------------------------------------------
[COLOR="Red"]**Generator is a Sega Genesis / Mega Drive emulator**[/COLOR]
------------------------------------------------------------------------

This is a modified version of [Generator by James Ponder]("http://www.squish.net/generator/") based on version 0.35.

More information is available [here]("http://www.ghostwhitecrab.com/generator/")

[LIST]
[*]Support for BZIP2, GZIP and ZIP compressed ROMs i.e., no more manual decompression or wasted disk space. Yay! 
[*]Support for X11's XVideo hardware acceleration by SDL for faster and smoother graphics. 
[*]Fullscreen support with or without the classic color frame. 
[*]SDL audio support (in favour of OSS Audio) which means you can use ESound and others for sharing the sound device among other applications. 
[*]Optional mute playing i.e., if you don't have a soundcard or the soundcard is busy you can still play. 
[*]Support for 48kHz sample rate (needs driver support). 
[*]Automagic CPU usage reduction which is especially cool for notebooks. The unpatched Generator uses more or less as much CPU as it can get even if needs far less than 10% on any modern system. 
[*]Working support for Game Genie codes.
[/LIST]


**[SIZE="3"]NOTE[/SIZE]**

- When building this package, I used the --with-raze --with-sdl-audio --with-gtk flags. 
- I have added my own launcher icon which appears in the KDE or GNOME menu


**[SIZE="3"]Supported OSes[/SIZE]**

Dapper Drake - [COLOR="Lime"]WORKING[/COLOR]
Edgy Eft - [COLOR="Lime"]WORKING[/COLOR]
Feisty Fawn - [COLOR="Lime"]WORKING[/COLOR]


[SIZE="3"]**TIP!**[/SIZE]

- After opening a ROM with the open ROM dialog box, you must **go to the Emulation menu and select Play!**


[SIZE="3"]**How to install**[/SIZE]

Download my Generator package here:

[http://www.zshare.net/download/generator_0-35-cbiere-r3_i386-deb.html](http://www.zshare.net/download/generator_0-35-cbiere-r3_i386-deb.html)

Install it with

```
sudo dpkg -i generator_0-35-cbiere-r3_i386.deb
```

Uninstall with

```
sudo aptitude remove generator
```


[SIZE="3"]**Other packages**[/SIZE]

**RPM (SUSE, Fedora etc)**
[http://www.zshare.net/download/22490415614271/](http://www.zshare.net/download/22490415614271/)

**Source code**:
[http://www.zshare.net/download/generator_0-35-cbiere-r3_i386_src-zip.html](http://www.zshare.net/download/generator_0-35-cbiere-r3_i386_src-zip.html)



**[SIZE="3"]You may also like my Gens emulator package, available here:[/SIZE]**

[http://ubuntuforums.org/showthread.php?t=290008](http://ubuntuforums.org/showthread.php?t=290008)

---

### Post by DoktorSeven on 2007-05-22
Runs here (Feisty 32-bit).  Trying to open a ZIP-compressed ROM doesn't work though (opens fine in Gens).

---

### Post by megamaced on 2007-05-23
The joypad support seems a little sketchy. My Saitek P880 only worked after I changed the keyboard configuration and hit the save button. I could only configure keyboard keys. I couldn't change the control mappings by pressing the buttons on the joypad. But my joypad works now, but I can't change the button mappings for it. It's also ashame that Generator only supports 3 buttons.

Generator seems a little faster then Gens. But it's just not polished enough to compete with Gens. The game compatibility doesn't seem as good either

---

### Post by dpzektor on 2007-05-23
Yeah, Gens is better, but still, it is nice to have another option. Thanks for the package!

---

### Post by Naegling23 on 2007-05-23
It installs and runs on kubuntu feisty here.  I'm currently trying to get it running from the command line.  This looks very promising, im trying to get a genesis emulator that can run from the command line (for mythtv) currently, the only one that exists is xe, but it doesnt have save state support.

Im liking this package, I'll keep plugging away trying to get it set up just right.

---

### Post by megamaced on 2007-05-24
> **Naegling23 said:**
>  I'm currently trying to get it running from the command line. 

I am not sure if you can run this emulator from the command line, because I compiled in the GTK interface. You could always download the source and compile without the --with-gtk switch :)

I'll play around with it a bit later. I might compile a command line only debian package too

---

### Post by hanzomon4 on 2007-05-25
Works here, and considering the fact that gens appears to be dead....

For those wondering how to run it:```
generator-gtk
```

---

### Post by megamaced on 2007-06-12
Added an RPM package for any SUSE or Fedora user that might be passing through. It's built using Alien, so I cannot predict the quality of the package. Seems OK on SUSE though.

Get it here:

[http://www.zshare.net/download/22490415614271/](http://www.zshare.net/download/22490415614271/)

---

### Post by pumex on 2007-06-28
2.12 works fine thanks men, but  2.13 cvs hangs and close after few seconds

---

### Post by Frem on 2007-06-28
It seems to run Sonic & Knucles more or less fine but there are some wierd issues. The video separates from the main window and goes into it's own little subwindow. Is that supposed to happen? Also, the sound has a half-second lag time.

edit: tried to use 2x window size, and the following came up. The Invalid memory fetch and access errors went for like 10 pages (out of the buffer of my terminal, so here's the end of it.

[CRIT ] 00000000 [ROM] Invalid memory fetch (word) 0x9C64
[CRIT ] 00000000 [MEM] Invalid memory access to ROM 0x9C64
[CRIT ] 00000000 [ROM] Invalid memory fetch (word) 0x9C68
[CRIT ] 00000000 [MEM] Invalid memory access to ROM 0x9C68
[CRIT ] 00000000 [ROM] Invalid memory fetch (word) 0x9C6C
[CRIT ] 00000000 [MEM] Invalid memory access to ROM 0x9C6C
[CRIT ] 00000000 [ROM] Invalid memory fetch (word) 0x9C70
[CRIT ] 00000000 [MEM] Invalid memory access to ROM 0x9C70
[CRIT ] 00000000 [ROM] Invalid memory fetch (word) 0x9C74
[CRIT ] 00000000 [MEM] Invalid memory access to ROM 0x9C74
[CRIT ] 00000000 [ROM] Invalid memory fetch (word) 0x9C78
[CRIT ] 00000000 [MEM] Invalid memory access to ROM 0x9C78
[CRIT ] 00000000 [ROM] Invalid memory fetch (word) 0x9C7C
[CRIT ] 00000000 [MEM] Invalid memory access to ROM 0x9C7C
[CRIT ] 00000000 [ROM] Invalid memory fetch (word) 0x9C80
[CRIT ] 00000000 [MEM] Invalid memory access to ROM 0x9C80
[CRIT ] 00000000 [ROM] Invalid memory fetch (word) 0x9C84
[CRIT ] 00000000 [MEM] Invalid memory access to ROM 0x9C84
ERROR: Something has gone seriously wrong @ 00009C88

---

### Post by megamaced on 2007-06-29
The emulator is designed so that the ROM window is seperate from the menu window.

In regards to your problems, I am not the maintainer. I only package Generator! You could file a bug on the Generator website.

---

### Post by jw5801 on 2007-08-02
64-bit version?

EDIT: Tried --force-architecture, rom didn't display properly (screen flickered alot). Might try compiling later.

EDIT 2: Would try compiling from source, except the source package is no longer there!

---

### Post by megamaced on 2007-08-02
There were too few people downloading the source package so it expired on Zshare. I'll upload it again later if I get time

---

### Post by JacobRogers on 2008-03-12
installed for me but when I tried to play Donald Duck Quack Shot it started playing but when I maximied the window it went insane.  So I'm gonna uninstall and look into this "Gens" program.

---

### Post by mrThefter on 2008-08-16
is there a specific reason libglib1.2 is dependency? libglib1.2ldbl replaces it.

Anyway, should be recompiled under libglib2.0 for hardy and up. As far as I can tell, anyway.

---

### Post by LeftyF on 2008-11-26
Tried to download this from the link but it just loops back and forth between "your downlaod will begin shortly" and "click here to download" (greasy file download site!). Is there another (less seedy) place to download this package?

---

### Post by wingnux on 2008-11-27
"Rise from your grave!" - Altered Beast


This thread is really old, you should use Gens/GS instead [http://ubuntuforums.org/showthread.php?t=959074&highlight=gens](http://ubuntuforums.org/showthread.php?t=959074&highlight=gens)

---

