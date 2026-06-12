---
title: "Urban Terror 4.1 + Minimizing Issues?"
date: 2008-01-04
forum: Gaming &amp; Leisure
---

### Post by haze. on 2008-01-04
Hi;

I am having issues with URT41.  I had previously installed URT40 with no issues, but the updated version seems to always minimize when I play the game for any length of time.  I then have no choice to ALT TAB back into the game or exit it completely, my only option is to restart my computer.

Any suggestions?  Is this happening to anyone else?

I have re-installed both URT41 and Ubuntu 7.10 and the same issue seems to happen.

Thanks.

Haze.

---

### Post by BreathEasy on 2008-01-04
Turn off Compiz Fusion. It's the primary cause of most of these issues with fullscreen games.

Before running URT, press ALT+F2 and enter

metacity --replace

Now you can run URT without trouble. Once you're done, press ALT+F2 again and enter

compiz --replace

to get Fusion going again. There's at least one tutorial around which shows how to write a script which can disable/enable Compiz when running specific programs.

---

### Post by haze. on 2008-01-04
thanks for the reply.  what is compiz fusion?

I will try that out and let you know how it works.

---

### Post by BreathEasy on 2008-01-04
Compiz Fusion is the name of the advanced windowing manager included in Ubuntu 7.10. It's the thing responsible for all the fancy wobbly window/spinning 3d cube crap on the desktop. :)

Although I use it myself, it has a tendancy to either slow down fullscreen games, or affect them in other ways, such as here with the minimizing. Some games run just fine with it, others don't, so I tend to disable Fusion just before running a game, then turn it back on afterwards. Gives me maximum frame rate anyway by turning it off.

---

