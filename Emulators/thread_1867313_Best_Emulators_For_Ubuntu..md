---
title: "Best Emulators For Ubuntu."
date: 2011-10-22
forum: Emulators
---

### Post by Exovolt on 2011-10-22
Hi, first time posting so apologies if this is the wrong forum. Myself and a friend have decided to build a mini ITX PC into a Mega Drive casing with the intention of using it as an emulator box (pics when it's finished). It's at the point where all the major components are installed but we need to find the emulators themselves so does anyone have (or has a link to) a list of the best emulators on Ubuntu for Mega Drive, SNES etc?

---

### Post by Alwimo on 2011-10-22
"Gens/GS" is a Mega Drive emulator that works in 32-bit but not 64-bit.

---

### Post by WienerWuerstel on 2011-10-22
There are many great Emulators that run natively on Linux but it's hard to find them all If you don't know the Names. So I will make a List for you because I can :P.

Nintendo Entertainment System: [FakeNES]("http://fakenes.sourceforge.net/svn/"), [halfnes]("http://code.google.com/p/halfnes/")

Super Nintendo Entertainment System: [Zsnes]("http://www.zsnes.com/"), [bsnes]("http://byuu.org/bsnes/")

Nintendo 64: [mupen64plus]("http://code.google.com/p/mupen64plus/")

Gamecube and Wii: [Dolphin]("http://www.dolphin-emulator.com/")

Game Boy Color/Advance: [VBA-M]("http://vba-m.com/")

Sega Master System and Sega Game Gear: [Osmose]("http://bcz.asterope.fr/")

Sega Genesis: [Kega Fusion]("http://www.eidolons-inn.net/tiki-index.php?page=kega"), [Gens/GS]("http://segaretro.org/Gens/GS")

Playstation: [PCSX-R]("http://pcsxr.codeplex.com/")

You can find them either in the Repos, PPA's or on the Emulator Website. If you want to know some Emulators for other Systems just let me know ;)

---

### Post by Radical_Dreamer on 2011-10-26
epsxe works well and it does have linux for it although I have yet to try it with linux (just windows).

---

### Post by satanselbow on 2011-10-26
> **Radical_Dreamer said:**
> epsxe works well and it does have linux for it although I have yet to try it with linux (just windows).

pcsxr is a much better native choice on linux. epsxe linux version is old. There are several thread on the forum reporting better success running the windows version under wine.

---

### Post by Radical_Dreamer on 2011-10-27
By the way, what works best for Nintendo DS?

---

### Post by collisionystm on 2011-10-27
I suggest hooking an Xbox controller up to the machine to play your games ;)

---

### Post by thatguruguy on 2011-10-27
> **Radical_Dreamer said:**
> By the way, what works best for Nintendo DS?

DeSmuME.  It's in the Ubuntu Software Center.

---

### Post by weasel fierce on 2011-11-01
Fusion is amazingly awesome for Sega Megadrive/Genesis stuff. I believe it also does Master System but I don't know if I ever tested it.

If you want retro computer emulation too, UAE works well for Amiga but can be a bit hardware intensive. Vice is outstanding for C64 and earlier. It took a bit of fussing around to get it running though.

---

### Post by blackadam on 2011-12-27
I have download GFCE Ultra NES and ZNES emulator and can manage to play the games.

how do i save?? i saw someone said press number key then f5 (what it does is close the emulator screen) to save but when i go to load it f7 says error loading save state and wont load :/


how can i connect my ps3 controller to be able to use it with a usb cable??

---

### Post by blackadam on 2011-12-27
hey mmm...wiener... sorry :P whats the terminal code to download the PCSX-R emulator. im new to linux so whenever i click on links to download something they never work right sorry for the hassle

---

### Post by WienerWuerstel on 2011-12-30
> **blackadam said:**
> hey mmm...wiener... sorry :P whats the terminal code to download the PCSX-R emulator. im new to linux so whenever i click on links to download something they never work right sorry for the hassle


Oh sorry for the late Answer but here you go:
```
sudo apt-get install pcsxr
```

---

### Post by brencameron on 2012-01-28
Radical_Dreamer had asked about the Nintendo DS. 

For 32-bit, DeSMuME seems to work fine. It feels a little slow on my machine, and the sound is so slowed down that I ended up turning it off. You should try it, you might have better results (my laptop is 2 1/2 years old and wasn't a high-end rig). Desmume is in the getdeb repositories, so you'll need to enable them. It opens in a smallish window - I suggest expanding the window to fill your screen if you want to read text.

---

### Post by FrodeSolheim on 2012-05-01
This is a bit of a shameless plug, but: FS-UAE is a quite new, and good Amiga emulator based on updated emulation core from WinUAE :) I have just released version 1.2 here: [http://fengestad.no/wp/fs-uae](http://fengestad.no/wp/fs-uae) (And I provide precompiled Ubuntu/Debian debs).

---

### Post by mister_playboy on 2012-05-24
Snes9x was not mentioned for Super Nintendo, but I think it's the best choice for most users.

ZSNES is a pain to install and has a much lower level of compatibility and sound quality than the others.

bnes is quite resource intensive and the current default GUI is lackluster... byuu is hoping to get someone else working on that part. :p

You can install/update snes9x easily from this PPA, run by the emulator's Linux developer: [https://launchpad.net/~bearoso/+archive/ppa](https://launchpad.net/~bearoso/+archive/ppa)

---

### Post by Hari5g900 on 2012-06-07
What about DOSbox?

---

### Post by thatguruguy on 2012-06-07
> **Hari5g900 said:**
> What about DOSbox?

The OP was really asking about emulating console games.

---

### Post by Hari5g900 on 2012-06-10
Oh yeah OK. Sorry!:lolflag:

---

### Post by mcchedder on 2013-02-20
ya its [http://www.coolrom.com/](http://www.coolrom.com/)

---

### Post by Linuxgamer94 on 2013-07-31
Hm, padon me, but the OP said that he was making a Linux box in the case of a Sega Genies. So if it is based on Ubuntu or Mint all you have to do is plug in your USB controler. Now you will probaly need a keyboard and mouse at first to set up the emmulators as most of them do not have any auto detection on them. Also Kega Fussion is now dead on Linux so you will have to use a version of Gens/GS and it does work on 64bit machines as I used it this morning at 9:00 AM to make sure it  worked, I had to drown out those talk shows on Channel 8. If you want a classic experiance you can also get some USB converters or ports that let you plug in a Mega Drive contoler to your computer through the USB port.

---

### Post by NotCras on 2013-10-04
Mind if I piggy back on this thread? How's ps2 emulation looking on linux?

---

### Post by Nano_ext3 on 2014-05-07
Has anyone gotten Gens GS II to work?

---

### Post by General_Faliure on 2014-05-08
Don't forget Daphne, the laserdisc emulator.
Although it takes a bit of effort to get it running on a modern 64 bit system (Lubuntu 14.04)

---

### Post by ZarathustraDK on 2014-05-19
Not to forget UME (Universal Machine Emulator). It's pretty much a conjoining of MAME and MESS, and will, ideally, play anything you throw at that there's an open source emulator for.

Sure it takes some tinkering to set up, but once you're comfortable with where which files go and editing the conf's, then it's a beast. I got Arcade-games, SNES, NES, Genesis, MegaCD and N64 working on it, haven't tried any of the million other systems it claims/aims to support.

---

