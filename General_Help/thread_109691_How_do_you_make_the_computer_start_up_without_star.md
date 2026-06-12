---
title: "How do you make the computer start up without starting X?"
date: 2005-12-29
forum: General Help
---

### Post by NPN_Transistor on 2005-12-29
How do you configure the computer to start up, but not boot up into X, just a text-only command prompt?

---

### Post by Koybe on 2005-12-29
i would say
```
sudo update-rc.d -f gdm remove
```

---

### Post by chaumurky on 2005-12-29
that'll do it ;-)

---

### Post by NPN_Transistor on 2005-12-29
Thanks for the help. Afterwards, how would I set it back to normal (make it boot up into X again)?

---

### Post by chimera on 2005-12-29
sudo gdm

---

### Post by Koybe on 2005-12-29
[QUOTE=NPN_Transistor]Thanks for the help. Afterwards, how would I set it back to normal (make it boot up into X again)?[/QUOTE]
i would say
```
sudo update-rc.d gdm defaults
```

---

### Post by purpleturtle on 2005-12-29
How about changing the default run level to 3?

I think this is set in /etc/inittab

---

### Post by danderson3 on 2006-10-12
I can't get to a console terminal no matter what I do.  The
ctl-alt-fx keys take me to a black screen.  I have a script
which supposedly can reset the screen from that condition, but
it must be run first in a console ( apparently _not_ an xterm )
one time initially to save a known good state.  I used update-rc.d
and landed in the same condition, which left me with an unuseable
system - thanks to ssh for letting me in to reverse that and restore
gdm!  Right now I am running with runlevel 3 as the default, which
appears to have no effect.  There is something basic wrong with my
machine!  Any help would be appreciated...

David

---

