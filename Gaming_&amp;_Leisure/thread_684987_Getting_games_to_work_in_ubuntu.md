---
title: "Getting games to work in ubuntu"
date: 2008-02-01
forum: Gaming &amp; Leisure
---

### Post by WadiJM on 2008-02-01
Hi all, I'm trying to use only ubuntu for all my task. Now I'm trying to run games, like play station I or play station II  so I downloaded some cso files but I do not know what else to do. First I tried to transform the cso to iso so I can mount it with  Gmount(I did the same with warcraft III but it didn't work). Any way, after downloading ciso, I tried to convert the cso to iso but I got an error "can't allocate memory" and  I have a 4 gb ram pc. So i'm really frustrated cause I didn't found any how to, all the how to tells me how to install de pcsx but it didn't say anything how to run it. I'm kind of lost and hopeless but if anyone have any idea it wold be great.
THanks in advance,
Wadi

---

### Post by sharperguy on 2008-02-01
Hi

As far as I know, Playstation 2 emulators are not in a useable state yet on any OS.

However Playstation 1 games should work (though I've never tried with ubuntu).

[http://ubuntuforums.org/showthread.php?t=612021](http://ubuntuforums.org/showthread.php?t=612021) -- This is a guide to installing epsxe which is the PS1 emulator I used under windows and it worked well.

---

### Post by KhaaL on 2008-02-02
instead of hassling with epsx, use [pSX]("http://psxemulator.gazaxian.com/") instead. it "just works".

And regarding PS2 emulator, I've been hassling with one for a while and eventually gave up on it. you best bet is snes and NeoGeo games for emulation

---

### Post by frenchn00b on 2008-02-02
easy to run :
[http://packages.dfreer.org/](http://packages.dfreer.org/)
 
pcsx &

---

### Post by FenderGuy2112 on 2008-02-02
~~~~~

---

### Post by WadiJM on 2008-02-02
Ok, I have Installed pcsx and mounted an iso with Gmount. I also downloaded a bios. But when I go to File->Run CD it prompts the configuration screen. No option is enabled, only the one to choose the bios.....What else should I do?Should I install someting else?
Thanks in advance,
Wadi

---

### Post by acoustibop on 2008-02-02
As people here have said, WadiJM -  don't bother with PCSX or ePSXe - both are difficult to get working properly in Linux, and are also very old - the last update for either was 1.6.0 for ePSXe, which was 4 1/2 years ago.

As people here have suggested, try pSX, which KhaaL has linked, and frenchn00b has linked dfreer's repository, which includes pSX and Ultima's Frontend - a really useful frontend for pSX - if you want to install them the 'proper' way.

In fact, most people just unpack the pSX download to their Home folder and play it that way.  The only requirements are working 3D videocard, working soundcard and libgtkglext1 (in the repositories) and there's very little configuration needed.  If you want to install [Ultima's Frontend]("http://psxemulator.proboards54.com/index.cgi?board=news&action=display&thread=1156715263") the same way, just unpack it to your new ~/pSX folder and run it.

pSX is still in active development - in fact, pSX Author (the developer) says he will be including video recording in the next release.  See the [official pSX forum]("http://psxemulator.proboards54.com/index.cgi").

**Edit:**  as far as Playstation 2 emulation is concerned, there is [PCSX2]("http://www.pcsx2.net/"), but you'll need a very high end machine to get games even running slowly ATM.  pSX Author is planning developing Playstation 2 emulation for pSX Emulator, but this probably won't be for a while yet.  It's likely, though, that when he does produce it, it'll be reasonably less resource intensive than PCSX2.  Apparently he already has one Playstation 2 game running ATM, but he won't say which one!

---

### Post by stoneage on 2008-02-02
PCSX2 Playstation 2 emulator is available from getdeb.net for 32 or 64 bit - 
[http://www.getdeb.net/category.php?id=3](http://www.getdeb.net/category.php?id=3)

---

### Post by WadiJM on 2008-02-03
Ok thanks, I got confused pSX with pcSX... Now I downloaded pSX . I'm trying to run some games but it throws an Error reading from .cue or sort of. Anyway thanks for the help,
Best regards,
Wadi

---

