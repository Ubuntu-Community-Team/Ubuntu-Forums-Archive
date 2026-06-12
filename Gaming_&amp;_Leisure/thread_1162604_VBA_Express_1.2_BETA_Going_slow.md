---
title: "VBA Express 1.2 BETA Going slow"
date: 2009-05-17
forum: Gaming &amp; Leisure
---

### Post by Zaxbeez on 2009-05-17
I recently downloaded VBA Express from the Add/Remove Programs list in Ubuntu, and I try to play PKMN Emerald on it. The game runs from 35%-75%, and the max I've seen it (With speed on) is about 90%. My settings on it are: No Fullscreen, No Interframe, No Filter, Frame Skip 2, no auto skip, 0 GB Frame Skip, video 1. The sound is on, running at 11Khz, and there are no Misc. Options selected. The volume is at 0. The Transparent Box is checked in the "Other" tab. I have no paths.

---

### Post by Zaxbeez on 2009-05-17
The odd thing is, it works perfectly with Gameboy games. Just not GBA games.

---

### Post by disturbedite on 2009-05-18
i'd recommend using vba-m instead since it continues development of vba.

[http://vba-m.ngemu.com/](http://vba-m.ngemu.com/)

---

### Post by Zaxbeez on 2009-05-18
> **disturbedite said:**
> i'd recommend using vba-m instead since it continues development of vba.

[http://vba-m.ngemu.com/](http://vba-m.ngemu.com/)

So where exactly is the download for that? I can't seem to find it.

---

### Post by Grishka on 2009-05-18
> **Zaxbeez said:**
> So where exactly is the download for that? I can't seem to find it.

look like they don't offer linux binaries for now. oh well, this one builds easy.
```
svn co https://vbam.svn.sourceforge.net/svnroot/vbam/trunk vbam
cd vbam
sudo apt-get install devscripts debhelper libgtkmm-2.4-dev libglademm-2.4-dev libgtkglextmm-x11-dev libxv-dev nasm
debuild
```

this will create a debian package for you.

edit: on a side note, gba emulation is quite demanding on computer resources, there is really no comparison to gb and gbc emulation. if your system is not up to it, this will be slow anyway.

---

### Post by Zaxbeez on 2009-05-19
I put in that code, and it started working about 85-95% on GBA games. It's weird now though because it only works on 2 or 3 GBA Games.

---

### Post by Grishka on 2009-05-19
> **Zaxbeez said:**
> I put in that code, and it started working about 85-95% on GBA games. It's weird now though because it only works on 2 or 3 GBA Games.

oops, guess this wasn't clear enough. I'm not sure what you're doing, but you have to uninstall vba express and vba first. that code I gave should've created a .deb file in your home directory, called vbam(something).deb. it's an installation package, simply double click and install. now, vbam itself has no gui, it has to be run manually. just set .gba extension to open with "vbam -F" or something. type "man vbam" from the terminal to see all options.

---

