---
title: "poweroff does not work on shutdown"
date: 2006-10-07
forum: Desktop Environments
---

### Post by www.rzr.online.fr on 2006-10-07
The ATX poweroff call does not work on shutdown... should I load a special module for my main board : Apollo KT266

I remember it used to work when I was on debian ...

more details may comes at :
@ [http://rzr.online.fr/q/VIA](http://rzr.online.fr/q/VIA)

---

### Post by Old Pink on 2006-10-07
So your system hangs at system halt?

Hmm... I've seen a thread about this before. Search around, it's on here. I'll edit this post if I find it. :)

[B]Edit:
[/B][http://ubuntuforums.org/search.php?searchid=8689535](http://ubuntuforums.org/search.php?searchid=8689535)
[http://ubuntuforums.org/showthread.php?t=237325&highlight=won%27t+halt](http://ubuntuforums.org/showthread.php?t=237325&highlight=won%27t+halt)
[http://ubuntuforums.org/showthread.php?t=268107&highlight=won%27t+halt](http://ubuntuforums.org/showthread.php?t=268107&highlight=won%27t+halt)

Can't halt won't halt! Seems to be fixed by putting acpi=force in the boot command line in GRUB.

---

### Post by www.rzr.online.fr on 2006-10-08
that's it thank you matt

---

### Post by www.rzr.online.fr on 2008-02-17
But I have to do edit menu.list on each update ...
how to overide this for ever

---

