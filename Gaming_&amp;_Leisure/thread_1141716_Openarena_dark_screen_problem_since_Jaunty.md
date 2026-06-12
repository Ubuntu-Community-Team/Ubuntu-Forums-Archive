---
title: "Openarena dark screen problem since Jaunty"
date: 2009-04-28
forum: Gaming &amp; Leisure
---

### Post by Jameshardy88 on 2009-04-28
Hi, ever since ive upgraded to jaunty  ive had this problem with openarena where after a short time of play (does not seem to be a set amount of time) my screen gets alot darker, to the point where it is hard to see what is going on. Does anyone know wat might be causing it?

---

### Post by gpeck157 on 2010-05-10
My OpenArena worked fine in 9.10 but since installing (fresh) 10.04 my OpenArena is almost unplayable due to the same thing. I fiddled with a number of settings inside the game, but nothing seems to help the dark screen.

---

### Post by gpeck157 on 2010-05-11
Well I found a simple solution to my dark screen problem. I have an old laptop (HP zd-7000) with an ATI graphics card. It could not handle OpenArena and the Appearance animations etc. at the same time. I went into System>Preferences>Appearance>Visual Effects. I selected "None". After rebooting, OpenArena worked just fine (and I could see the darn screen!)

---

### Post by R33D3M33R on 2011-02-19
The solution is to open q3config.cfg and set/change this lines:

```

seta r_mapoverbrightbits "10"
seta r_overbrightbits "0"

```

---

