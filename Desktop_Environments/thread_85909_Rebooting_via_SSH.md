---
title: "Rebooting via SSH"
date: 2005-11-03
forum: Desktop Environments
---

### Post by seethru on 2005-11-03
Is anyone able to do this? No matter what command I use, sudo reboot, sudo reboot -f, sudo shutdown -r now, it doesn't actually restart. Any help is greatly appreciated.

---

### Post by RAOF on 2005-11-03
Well, I just tried it, and sudo shutdown -r now worked.  So at least someone's able to do it ;)

---

### Post by kvidell on 2005-11-03
What does the following get you?```
sudo telinit 6
``` ?

That should change the init runlevel to 6, or "reboot", the hardcore way.
- K

---

### Post by seethru on 2005-11-03
[QUOTE=kvidell]What does the following get you?```
sudo telinit 6
``` ?

That should change the init runlevel to 6, or "reboot", the hardcore way.
- K[/QUOTE]
That did it, waiting for it to come back online.

---

### Post by kvidell on 2005-11-03
[QUOTE=seethru]That did it, waiting for it to come back online.[/QUOTE]
I don't know if it's recomended to do that as your main way of rebooting... I'm not sure if there's anything it _doesn't_ do that "reboot" or "restart" (whatever the command is, I don't know) does...

It's just the low level grunt way of doing it that almost always works when nothing else does.
It's what I use... I'm the only user so I don't need any of the "alert" functionality of the other stuff and if there's anything it doesn't do.. well... I haven't noticed any negative side effects from it, so I'ma keep doing it :-D

Glad it worked for ya... It's strange that the other methods didn't, though... as basically all they are are interfaces with optional "features" that boil down to eventually executing at "telinit 6" after some other scripts are run (I'm assuming they run scripts, I dunno).

- Kev

---

