---
title: "GDM fails to start, booted straight to console"
date: 2006-09-24
forum: Desktop Environments
---

### Post by moon_dog on 2006-09-24
i got this error when i rebooted my computer.  this happened right after i tried to install xgl/compiz, before finding out that they were removed from the repos.

```
GDM: Xserver not found: /usr/bin/Xgl :0 :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo -kb -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
error: command could not be executed
```

it then tells me to reconfigure gdm.

anyone know what to do?

---

### Post by wombat20 on 2006-09-24
I think you should try this:
```

sudo dpkg-reconfigure xserver-xorg

```

If you have any trouble go for the VESA option as it seems the "safe" one.  Hope someone who understands can explain this a bit more clearly than me.

---

### Post by moon_dog on 2006-09-24
already tried that, still get the same error.  it happened after i tried to install xgl/compiz, i think it has something to do with that.

---

### Post by Flaringo on 2006-09-24
Hello!

I had the same problem. When you were setting up XGL/Compiz, you probably edited the gdm-conf-custom file. What you have to do now, is to delete the content you added there earlier -- under [servers]. So boot up Ubuntu, log in and type "startx". Yes, you can still run X! So, you type sudo gedit /etc/gdm/gdm.conf-custom in the console, and delete ```
0=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo -kb
flexible=true
``` <---- That

I hope this helps!

-- Flaringo

---

### Post by moon_dog on 2006-09-24
dude you're a genius!! that fixed it!! thanks a lot.

---

### Post by Flaringo on 2006-09-24
I'm glad I could help! :D

---

