---
title: "Xmame exe, no can find"
date: 2006-06-03
forum: Gaming &amp; Leisure
---

### Post by RotoGrip on 2006-06-03
GXmame no longer findes xmame executable.](*,)  Is this because of the Dapper release? Ive uninstalled and reinstalled through Synaptic. But i keep getting the same thing. Is there hope for Mame in Dapper?

---

### Post by DoktorSeven on 2006-06-03
What does

```

which xmame

```

give you from a terminal window?  If you get a path, you should be able to feed that entire path into gxmame's configuration...

(mine's in /usr/games/xmame, by the way)

---

### Post by RotoGrip on 2006-06-03
Thanks Doktor, you solved my problem

---

### Post by Onyros on 2006-06-04
I'm having a few problems setting up xmame in Dapper. I can only use xmame-sdl, and the graphics come out quite pixellated. xmame-svga doesn't work, and xmame-x just gives me a black screen (from which I have to CTRL+F1).

I have a X700 well setup with fglrx drivers (getting around 4200 fps in glxgears, so I guess 3D acceleration is working fine and dandy).

Another strange thing, I love the GL-Matrix screensaver, but it's coming out very very slow. And yet another strange thing, I can play TORCS perfectly, getting 150 fps at times, but Foobillard is virtually unplayable...

Any general ideas on why this may be happening?

---

