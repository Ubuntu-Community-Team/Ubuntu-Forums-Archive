---
title: "Mouse problems in games"
date: 2009-11-02
forum: Gaming &amp; Leisure
---

### Post by eragon100 on 2009-11-02
Hello!

I have a problem with the new ubuntu 9.10 Karmic Koala :(

The mouse does not work correctly in games. The cursor moves OK, but when I click a button, it jumps to the bottom right of the screen, and nothing else happens. I have only tested Shadowgrounds Survivor and Nexuiz so far, but it happens in both these games :(

Does anyone know of a way to fix this?

Thanx! :popcorn:

---

### Post by donkyhotay on 2009-11-02
What kind of games are you talking about? If you're uncertain please give some example games where this has been happening.

---

### Post by eragon100 on 2009-11-02
> **eragon100 said:**
> Hello!

I have only tested Shadowgrounds Survivor and Nexuiz so far, but it happens in both these games :(

Does anyone know of a way to fix this?

Thanx! :popcorn:

Like those examples :D

Both are 3d accelerated games. Was there not some new version of an input system or something in 9.10? Something called "X input" or what? Maybe that is the problem :confused:

---

### Post by donkyhotay on 2009-11-02
Sorry, didn't see the names of the games listed in your OP. I haven't had any problems with any of the 3D games I play (savage 1&2, bzflag) and I have karmic installed. I'll check out nexuiz since I do occasionally play it from time to time (just haven't gotten to it since the upgrade) and tell you what I get.

---

### Post by eragon100 on 2009-11-02
I have the problem in Savage 1: XR as well, I just checked it :(

Cool game by the way :popcorn:

---

### Post by eragon100 on 2009-11-03
I can not play unreal tournament either, does anyone have a suggestion?

EDIT: The mouse also does not work if I set nexuiz to windowed mode :(

EDIT 2: Unplugging the mouse and then plugging it into a different USB port doesn't help either :(

---

### Post by eragon100 on 2009-11-03
Okay I found out something new: Eschalon book 1 and battle for wesnoth do work. Wesnoth is not a 3d game, but Eschalon is. It does, however, not use SDL. Since I have seen other problems and two bug reports on launchpad describing problems with the mouse in games that use SDL (and only in games that use SDL), I figure the problem is in that library. I have never had this problem before, also not in Jaunty. Does anybody have an idea how to fix sdl?

EDIT: FIXED!! :D

Found this on Arch forums:

export SDL_VIDEO_X11_DGAMOUSE=0 in a terminal prior to starting a game will fix uncontrollable mouse issues.

A permanent solution is also given on the Arch forums:


    "However, a permanent solution that works for all games, is to add the following to the Modules section of your xorg.conf file:
    Code:

    # Load "extmod" but omit DGA extension
    SubSection "extmod"
        Option "omit xfree86-dga"
    EndSubSection

Try editing the /etc/X11/xorg.conf file. :)"

---

