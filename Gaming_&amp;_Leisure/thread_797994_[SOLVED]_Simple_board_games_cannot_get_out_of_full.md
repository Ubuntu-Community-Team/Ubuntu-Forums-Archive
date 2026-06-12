---
title: "[SOLVED] Simple board games cannot get out of fullscreen"
date: 2008-05-17
forum: Gaming &amp; Leisure
---

### Post by VMC on 2008-05-17
If you go to:
Applications > Games > AisleRiot Solitare and Freecell Solitare

Those two when put in full screne, it won't allow you to go back to normal screen. I have to type ALT+F4. I checked and nothing in /usr/games. Does anyone know where the init files would be? Thanks

PS- Chess, Blackjack work okay.

---

### Post by Bufke on 2008-05-17
Doesn't happen to me.  I can just click exit full screen.  Maybe you disabled the bar?  You should be able to exit full screen with F11

---

### Post by VMC on 2008-05-17
> **Bufke said:**
> Doesn't happen to me.  I can just click exit full screen.  Maybe you disabled the bar?  You should be able to exit full screen with F11

I tried that, using F11. The screen just blinks and still full screne. Some parameter somewhere is mess up. I don't hink its xorg because the other board games work correctly. but thanks for the reply.

---

### Post by VMC on 2008-05-17
The problem is that even at full screen their is a top border that you can revert back. The two mentioned games don't show that. So here is how I managed to fix it. I thought it had something to do with screen resolution, so I changed my screen size from 1024x768 to 800x600 and then when I ran the two mentioned games they went back to normal.I then reverted back to 1024x768 and it was back to normal! Strange.

---

