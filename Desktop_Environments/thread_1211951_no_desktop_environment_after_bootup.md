---
title: "no desktop environment after bootup"
date: 2009-07-13
forum: Desktop Environments
---

### Post by bryncoles on 2009-07-13
its more an annoyance than a problem... i got hit by the jaunty freeze-bug. i 'resolved' it by running ```
metacity -- replace
```. now, some updates have fixed the bug for me. yay! but, when i boot up my computer now, i have to reload compiz before the desktop displays (even after running compiz -- replace). 

anyone able to help me?

---

### Post by bryncoles on 2009-07-14
bumpo!

---

### Post by bryncoles on 2009-07-18
bump?

---

### Post by ~sHyLoCk~ on 2009-07-18
Add this ```
compiz --replace &
```
in your System->preferences->startup applications

---

### Post by bryncoles on 2009-09-02
> **~sHyLoCk~ said:**
> Add this ```
compiz --replace &
```
in your System->preferences->startup applications

Finally got round to following this up....

The above suggestion doesn't work for me! boo! I'll explain the problem in a little more detail:

I got hit by the flash/freeze but when I upgraded from 8:10 to 9:4. At that time, the release notes recommended turning compiz off, switching to metacity or something like that. 

For me, the command ```
metacity --replace
``` as good as fixed the issue, with minimal compromise from my compizzing. I could live with it. 

Now the freeze issue is resolved (as far as I can tell, and at least for me it is). However, running ```
compiz --replace
``` has not restored compiz at boot. I have to reload the window manager after booting before I'm good to go. Adding 'compiz --replace' to my start up services was a good idea, but seems to have had no effect. 

Any other ideas please?

---

### Post by bryncoles on 2009-09-03
Bump? anyone?

---

### Post by bryncoles on 2009-09-04
Brrrrrrrrrrrrrrump!

---

### Post by bryncoles on 2009-09-07
booompa

---

### Post by UbuntuNerd on 2009-09-07
so you want "compiz" to start at boot up?

---

### Post by bryncoles on 2009-09-08
That sounds right! yes!

---

