---
title: "ROM Compressor"
date: 2007-11-25
forum: Gaming &amp; Leisure
---

### Post by kevindubrow on 2007-11-25
Hi, just to start off...I own the game this ROM is for.

I have a hack for a ROM, I need a compressor so I can combine the hack with the rom...if anyone knows of a program I can use, that would be great! Thanks.

Also...the hack is a .ips file. Thanks again!

---

### Post by FranMichaels on 2007-11-26
An expander you mean? Those are only needed if it is a big hack. 

What emulator do you use? mednafen and zsnes support soft patching.

i.e. yourgame.ext
      yourgame.ips
if you give the ips file the same name, in the same folder. it will patch when you load. 

I like this better because if there is a newer patch, you can just replace the ips file, and you don't have to to worry about your rom file being permanently modified.

If you want to hard patch it, last tool I used was [Lunar IPS]("http://www.romhacking.net/utils/240/") (freeware), It ran fine under wine. Keep a backup of the original game though.

---

### Post by kevindubrow on 2007-11-26
Well it is for a NES emualtor, GFCE Ultra NES Emulator. So the game is a .nes file and the hack is a .ips. All I would have to do is name both of the files the same, right? Thanks for your help.

---

### Post by FranMichaels on 2007-11-26
Should be, mednafen has some of its code based on fceu. 

If it doesn't work, you might need to name it like this (with the extension too)

game: thegame.nes
patch name: thegame.nes.ips

:)

---

### Post by kevindubrow on 2007-11-26
Ok, I'll give this a shot soon when I have time. I'll get back to you with the result. Thanks a lot!

---

