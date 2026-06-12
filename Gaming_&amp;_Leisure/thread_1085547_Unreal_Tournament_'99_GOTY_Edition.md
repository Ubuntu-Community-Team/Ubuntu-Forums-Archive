---
title: "Unreal Tournament '99 GOTY Edition"
date: 2009-03-03
forum: Gaming &amp; Leisure
---

### Post by fugazi32 on 2009-03-03
Hi, i've installed UT '99 GOTY with the native Loki installer, I installed with *sudo* but when I type '*ut*' to start the game I get:

```

lindsell@FUCKUP:~$ ut
/usr/local/bin/ut: 48: Bad substitution
dirname: missing operand
Try `dirname --help' for more information.
cd: 69: can't cd to System
/usr/local/bin/ut: 75: ./ut-bin: not found

```

I am now using Xubuntu 8.10, but i've had it working fine on SuSE 10.0 before. Also as I don't have a 3D effects card, I think I used software renderer or something is there a way I can edit the UT config to get those settings again, i've forgot to save my old UT config file!

EDIT: Okay, I can run the game with *sudo  /usr/local/games/ut/ut* but whenever I try to change the game's renderer it crashes??! Can still play it running sluggish with the OpenGL renderer.

---

### Post by fugazi32 on 2009-03-04
Bump.

Anyone got a sample *UnrealTournament.ini* file with low-res graphics settings & software renderer?

---

### Post by R33D3M33R on 2009-03-04
Read here, chapter 6: [http://www.lokigames.com/products/ut/downloads/README.436](http://www.lokigames.com/products/ut/downloads/README.436)

> Q: I want to use the Software Renderer.

A: Edit the following lines in either 
   (INSTALL_PATH)/System/UnrealTournament.ini or
   (HOME)/.loki/ut/System/UnrealTournament.ini

   To use the Software renderer:

   [Engine.Engine]
   GameRenderDevice=SDLSoftDrv.SDLSoftwareRenderDevice
   WindowedRenderDevice=SDLSoftDrv.SDLSoftwareRenderDevice
   RenderDevice=SDLSoftDrv.SDLSoftwareRenderDevice



---

### Post by fugazi32 on 2009-03-04
All gravy now, bless! :D

---

