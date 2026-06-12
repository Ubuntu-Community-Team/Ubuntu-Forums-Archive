---
title: "Gamma Correction Problems"
date: 2006-10-23
forum: Gaming &amp; Leisure
---

### Post by diepruis on 2006-10-23
Hey everyone, I'm having some trouble with my games: I'm unable to change the gamma correction option. I've noticed this problem with Warcraft III and Unreal Tournament. Both run under OpenGL. Is there some fix for this?

---

### Post by akurtz on 2006-10-26
I had the same problem running Deus Ex under Wine.  You can set the gamma manually using the 'xgamma' command like so: ```
xgamma -gamma 1.2
```

A setting of 1.0 is the default, so to return the gamma back to normal: ```
xgamma -gamma 1
```

I put these commands in a script to increase the gamma, launch the game, then restore the default gamma when exiting the game.  Hope this helps.

---

### Post by diepruis on 2006-10-26
Yeah, that ought to do it. Thanks a lot!

---

### Post by akurtz on 2006-10-26
Sure thing.  Happy gaming!

---

### Post by diepruis on 2006-10-26
Quick question, how do I get the script to wait after the program has exited to return the gamma to 1? Here's the script I tried, but it set the gamma to 1.7 and immediately back to 1.

```

xgamma -gamma 1.7
cd "/home/ashley/progfiles/Warcraft III/"
wine war3.exe -opengl
xgamma -gamma 1.0

```

What do I need to change?

---

