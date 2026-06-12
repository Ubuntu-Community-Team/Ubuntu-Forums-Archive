---
title: "Mouse Moves Itsel On FPS Games"
date: 2010-07-19
forum: Gaming &amp; Leisure
---

### Post by KingOfDeath on 2010-07-19
The Title Explaon It All.
My Mouse Cursor Moves To the center itself 
Im using a dell inspiron 1520
Thanks

---

### Post by J.K.Makowka on 2010-07-19
Hmm not sure what could be causing it.

Stupid idea: have you checked if you are not accidentally touch the touchpad with your palm while using the keyboard?

---

### Post by Åtta on 2010-07-20
I have the same problem, and no, it's not because I'm touching the touchpad.

---

### Post by KingOfDeath on 2010-07-21
Maybe a bug in Ubuntu 10.10 ?

---

### Post by hikaricore on 2010-07-21
Boot a live cd of an older version and see if it happens.

---

### Post by Åtta on 2010-07-24
> **hikaricore said:**
> Boot a live cd of an older version and see if it happens.

I don't have one lying around at the moment, but I didn't use to have this problem. In fact, I didn't use to have it in 10.04 either. It just started happening maybe a few weeks or months ago.

I just tried playing Smoking Guns, and I can confirm that it happens even if you're not running in full screen. It would seem that it happens in any game that captures the mouse.

---

### Post by Modplanman on 2010-07-24
One method of reading mouse movement in games actually relies on locking the mouse to a part of the screen (the centre and I think Urban Terror uses the top left), then reads any movement out from that point as far as I understand it. This may be related to that.

---

### Post by lasombra on 2010-07-26
Same here. Tried to play Sauerbraten and Nexiuz. In both games the mouse pointer moves always to a specific point (not necessarily the center of the screen).

I'm using Maverick Alpha 2 - yeah I know, it's alpha.

Edit:
At least in Nexuiz, I have the effect in full-screen and non full-screen mode. Did not try in other games

---

### Post by sadohound on 2010-07-30
I get this problem too.  Using Lucid 32bit & the mouse jumps back to the same spot whenever I try to move.  I've tried Urban Terror, Assault Cube & Nexuiz, all with the same problem (although jump to different spots in different games).  Strangely doesn't happen in Alien Arena, so is it to with the game engine (although I think UT & AA both use the same Quake 3 engine...)?

Any got an idea of a fix?  I've recently started using Unclutter to hide my mouse pointer, I'll try disabling this, see if it affects it.

---

### Post by scaine on 2010-09-10
sadohound, you rock.  This was doing my head in.  I've just bought Amnesia and got this problem... thought it was just Amnesia.  But then I tried Penumbra, which *was* working, and discovered it was doing the same thing!

```
sudo apt-get purge unclutter
```

Sweet.  Thanks.

---

### Post by pixnaps on 2010-11-22
I had this problem on all sorts of full-screen games (including dosbox games).  Uninstalling 'unclutter' fixed it.  Thanks!

---

