---
title: "Strange network lag in City Of Heroes"
date: 2007-05-02
forum: Gaming &amp; Leisure
---

### Post by kraz on 2007-05-02
The game installed fine, and it starts, runs and I get a good picture, no stuttering there.

But for some reason my character is moving too fast resulting in some strange lag. When i move, I keep getting sent back to the place I started moving from, or very near to it. this means moving anywhere in the game takes forever, and is rather annoying. This has been going on, since I Installed the game (running it under cedega 5.2).

I have no lag and network problems in wow, and Im on a 10MB cable connection. so I really wonder what it is, that causes this?

---

### Post by lordhebe on 2007-05-03
It's a cpu-scaling problem. Disable cpu scaling by typing ```
/etc/init.d/powernowd stop
``` as root in a terminal. To permanently solve the problem disable cpu scaling completely in you systems bios (AMD Cool 'n quiet, dunno what it is for Intel)

---

### Post by kraz on 2007-05-05
thanks a lot! that solved it!

---

