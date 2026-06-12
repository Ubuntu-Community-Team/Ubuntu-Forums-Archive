---
title: "How To EASY Install Gngeo 0.7 / Xgngeo 1.6 Final"
date: 2008-07-24
forum: Gaming &amp; Leisure
---

### Post by Sniffer on 2008-07-24
Hi fellows,

As retro games fan that i'm, here it's an EASY How to for you to install gngeo 0.7 with Xgngeo 1.6 Final.

1 - Download and Install gngeo 0.7 deb package bellow.

2 - Download the Xgngeo bellow and do this from the directory you download to:

sudo tar -vxjpf XGngeo-16.tar.bz2

cd XGngeo-16

sudo python setup.py install

NOW in the applications menu, there you have it XGngeo, when you enter the 1st time it will ask for you to give the right path to roms and bios.

Hope you enjoy this one

Regards
Sniff.

---

### Post by jpeddicord on 2008-07-25
Script + deb combination, moved to Gaming.

---

### Post by jimi_hendrix on 2008-07-25
whats gngeo?

---

### Post by Sniffer on 2008-07-25
> **jimi_hendrix said:**
> whats gngeo?

See Here:

[http://gngeo.berlios.de/](http://gngeo.berlios.de/)

I have made a deb package of the last version. Hope it help someone.

Sniff

---

### Post by jimi_hendrix on 2008-07-25
so its an emulator...is that legal?

---

### Post by Sniffer on 2008-07-25
> **jimi_hendrix said:**
> so its an emulator...is that legal?

YEP, develop an emulator is legal. Period.

---

### Post by jpeddicord on 2008-07-25
> **Sniffer said:**
> YEP, develop an emulator is legal. Period.

Emulators themselves are legal if they are used for legal purposes, such as exploring homebrew development. But I'll just say this in advance: any ROM/BIOS image requests or links will be removed and infracted.

---

### Post by Sniffer on 2008-07-25
> **jacobmp92 said:**
> Emulators themselves are legal if they are used for legal purposes, such as exploring homebrew development. But I'll just say this in advance: any ROM/BIOS image requests or links will be removed and infracted.

By my side you never will see that.

---

### Post by jimi_hendrix on 2008-07-25
but if its legal and roms/bios are illegal then what good is an emulator

---

### Post by FranMichaels on 2008-07-25
> **jimi_hendrix said:**
> but if its legal and roms/bios are illegal then what good is an emulator

Not all roms are illegal. Some have permission from the authors to be distributed. BIOS's can be re-implemented or reverse engineered. Not all emulators require bioses anyway. 

An emulator is emulating the hardware, so in that sense it keeps it from disappearing long after the original hardware fails / no longer made, you can think of running games on it as a side effect of "historical preservation" ;).

Anyway, if you'd like some homebrew games and demos, this site specifically hosts only roms that can be legally distributed.

[http://www.pdroms.de/](http://www.pdroms.de/)

---

### Post by jimi_hendrix on 2008-07-25
> **FranMichaels said:**
> Not all roms are illegal. Some have permission from the authors to be distributed. BIOS's can be re-implemented or reverse engineered. Not all emulators require bioses anyway. 

An emulator is emulating the hardware, so in that sense it keeps it from disappearing long after the original hardware fails / no longer made, you can think of running games on it as a side effect of "historical preservation" ;).

Anyway, if you'd like some homebrew games and demos, this site specifically hosts only roms that can be legally distributed.

[http://www.pdroms.de/](http://www.pdroms.de/)

thanks

---

### Post by GSZX1337 on 2008-07-25
> **jimi_hendrix said:**
> but if its legal and roms/bios are illegal then what good is an emulator

Game companies use remakes for releasing older games onto newer platforms (ie. the NES Classics for the GBA).

---

### Post by cyclone5uk on 2009-04-07
Followed the instructions, but everytime I try and open a game I get:

"This ROM is unloadable because Gngeo could not find any suitable driver to handle it."

All these roms work fine on my GP2X handheld (which also uses Gngeo).

---

### Post by Sniffer on 2009-04-16
> **cyclone5uk said:**
> Followed the instructions, but everytime I try and open a game I get:

"This ROM is unloadable because Gngeo could not find any suitable driver to handle it."

All these roms work fine on my GP2X handheld (which also uses Gngeo).

you have to do in terminal:

mkdir  /usr/share/gngeo/romrc.d -p ;  cp -a neogeo/gngeo-0.7/romrc.d/  /usr/share/gngeo/

hope it helps

---

### Post by Sniffer on 2009-04-16
> **Sniffer said:**
> you have to do in terminal:

mkdir  /usr/share/gngeo/romrc.d -p ;  cp -a neogeo/gngeo-0.7/romrc.d/  /usr/share/gngeo/

hope it helps

Take in consideration that in jaunty after you install gngeo will give this error

gngeo
gngeo: error while loading shared libraries: libSDL_image-1.2.so.0: cannot open shared object file: No such file or directory

to SOLVE THIS ONE INSTALL LIBSDL-IMAGE1.2 WITH SYNAPTIC, PROBLEM SOLVED.

Sniff

---

### Post by Liberator45 on 2010-01-24
Hi,

I'd like to uninstall this. It doesn't even open, and it seems like the icon is missing (and I'm not willing to resolve it). How do I install it?

Thank you

---

### Post by Liberator45 on 2010-01-26
Hi, can someone help me with this... please?

---

### Post by bhother on 2010-02-25
Thx.

bro i can install this ok, no problem now i can play my old neogeo roms ^^...

---

### Post by yanom on 2010-05-06
Eh, the .deb is for 32bit only... i have 64

---

### Post by bb93 on 2010-05-16
> **bhother said:**
> Thx.

bro i can install this ok, no problem now i can play my old neogeo roms ^^...

How did you that? I can't play, and i followed all instructions. 

Only appears: "This ROM is unloadable because Gngeo could not find any suitable driver to handle it."

---

### Post by andytof47 on 2010-08-24
yeah, have you got a 64bit? i have 64bit too
:p:p

---

### Post by MaximB on 2010-08-29
Can someone make/find a 64-bit version ?

The source installation doesn't creates all folders and doesn't run.

---

### Post by xunyicao on 2011-05-25
here is my problem :

Traceback (most recent call last):
  File "/usr/bin/xgngeo", line 39, in <module>
    execfile(os.path.join(package_dir, "__init__.py"))
IOError: [Errno 2] No such file or directory: '/usr/lib/python2.6/site-packages/xgngeo/__init__.py'


could you tell me how to solve it?thank you for your help

---

