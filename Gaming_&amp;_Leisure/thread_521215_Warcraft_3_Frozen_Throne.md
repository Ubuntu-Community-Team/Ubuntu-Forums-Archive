---
title: "Warcraft 3 Frozen Throne"
date: 2007-08-09
forum: Gaming &amp; Leisure
---

### Post by Jexel on 2007-08-09
Okay I'm running Warcraft 3 which is installed on my Windows Vista through Wine on Ubuntu Feisty. Everything works...however, the upper panel still exists whilst playing.

I cannot move the screen around as smoothly (by moving the mouse to the edges). How can I make it run in FULL SCREEN mode? In addition I have compiz-fusion installed so whilst moving my mouse to the top right it initiates the scale plugin.

Can anybody help me?

---

### Post by Swarms on 2007-08-09
Compiz Fusion doesn't support fullscreen games like Beryl did, so you have to switch to metacity instead while you play.

---

### Post by Jexel on 2007-08-09
how would i be able to switch over to metacity?

---

### Post by Swarms on 2007-08-09
I know you can type metacity --replace in the terminal but I don't know exactly how to switch back, tried compiz --replace, that did something but lead a lot of bugs.

If you got fusion-icon, a icon shaped like a blue box in your notification area, there you can switch freely.

---

### Post by Jexel on 2007-08-10
thanks a lot that helped greatly. I use "compiz --replace -c emerald &" to switch back to compiz. I was thinking...how would i be able to write a script that ran:

metacity --replace, followed by warcraft and finally running compiz-fusion only if Warcraft has exited?

---

### Post by Brezeck on 2007-08-10
just compiz --replace is okay

---

