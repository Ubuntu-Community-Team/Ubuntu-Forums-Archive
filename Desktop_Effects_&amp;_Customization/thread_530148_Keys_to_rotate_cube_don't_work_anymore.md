---
title: "Keys to rotate cube don't work anymore"
date: 2007-08-20
forum: Desktop Effects &amp; Customization
---

### Post by hpalma on 2007-08-20
I've just upgraded compiz-fusion to version 0.5.3 and as it seems i can't rotate the cube any more with the shotcut keys i defined.

I can still rotate it pressing CTRL+ALT+Button1. I just can't get the rotate-to-face keys to work. They worked fine in the previous version.

Any ideas ?

---

### Post by eskuge on 2007-08-20
I have the same problem. Using feisty fawn.

---

### Post by chriscl on 2007-08-20
I had the same issue after a recent upgrade. 

I found when looking in the compiz config settings manager, under "General Options" and "Desktop Size", the setting for "Horizontal Virtual Size" had got set back to '1'.

When I changed this to '4', and then restarted X (which of course restarted Compiz) normal service was resumed, and I was then able to rotate the cube again!

An odd one; you might want to check your compiz settings; many of mine seemed to have been set back to their 'default' values...?

---

### Post by hpalma on 2007-08-20
In my case it's not that. The cube is working fine. I can even rotate it using CTRL+ALT+LEFT or RIGHT. It's just the rotate-to-viewport keys that stopped working.

---

