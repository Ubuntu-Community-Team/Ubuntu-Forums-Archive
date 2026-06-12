---
title: "[SOLVED] another ut2004 prob (black screen, sound working)"
date: 2008-08-20
forum: Gaming &amp; Leisure
---

### Post by Lokian on 2008-08-20
Hi all,

it's about Unreal Tournament 2004...
I searched the forums but couldn't find any answers to my problem.

Whenever I try to start the game it loads(splash of UT2k4)
and then my screen turns black.
After that I read from my display: "mode not supported".

I hear the gamesound and when I move my mouse I hear the menus respond.
Sometimes I make it to exit UT2k4 blindly... :lolflag:

if not, I may kill UT over a virtual terminal but returning to X leaves me
with my "mode not supported".

My Computer:

OS: Hardy Heron 8.04 amd64(GNOME)
Graphic card: Geforce 6200 
(drivers work, direct rendering, installed via envy)
Monitor: 19" LCD.

thx in advance.

Regards,

Lokian

---

### Post by FrozenFox on 2008-08-21
It sounds like UT is trying to load into a higher resolution than your monitor can support. Try opening up your UT2004.ini file. It's probably in ~/.ut2004/System . Either that or User.ini in the same folder (i think ut2004.ini, but it never hurts to mention both) contain resolution settings somewhere. Also check the depth (16 vs 32 or whatnot).

If that doesn't work, you can try this, but it probably won't help: when the screen goes blank, do ctrl+alt+f2 and then go back via ctrl+alt+f7. If it's still black, this suggestion didn't work, which it probably won't.

---

### Post by Lokian on 2008-08-22
Hi again,

you had the right idea.

What I did:

edited ~/.ut2004/System/UT2004.ini
and changed it to a resolution working for me... (and I guess for many others too)

```

[SDLDrv.SDLClient]
FullscreenViewportX=1024
FullscreenViewportY=768

```

Thx,

Lokian

---

