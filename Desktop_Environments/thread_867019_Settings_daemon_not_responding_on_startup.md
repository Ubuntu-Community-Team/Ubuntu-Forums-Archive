---
title: "Settings daemon not responding on startup"
date: 2008-07-22
forum: Desktop Environments
---

### Post by yavamoni on 2008-07-22
Since a couple of days ago, I have the following problem: 

After I log in in the graphical interface, a grey box appears and stays there for a long time (before the background or panels are shown) Eventually (couple of minutes afterwards? much, much longer than normal startup) the grey box displayes the following message:

```
Ha ocurrido un un error al iniciar el demonio del Administrador de Preferencias de GNOME.

Algunas cosas como las configuraciones de temas, sonidos o fondo de pantalla puede que no funcionen correctamente.

El último mensaje de error fue:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME seguirá intentando reiniciar el Demonio de Preferencias la próxima vez que inicie una sesión.
```

It basically says there was a problem loading the settings daemon. 

I don't know how to check what's wrong that makes the daemon not respond, nor how to correct it. 

When I finally log in, I have the theme and keyboard layout changed.

I am on an  ASUS F9S laptop, using 64 bit ubuntu 8.04 updates up to date (22nd July 2008) - I suppose the problem appeared on an update

Any ideas how to fix this? 

Thanks!

---

### Post by mbutu on 2008-07-24
I have the same error... nelp

---

### Post by soluckytouselinux on 2008-07-24
someone help me pleeeeese. i get the message bus is not working. I love using ubuntu, I just need a push in the right direction. thanx in advance for any help

---

### Post by rothalem on 2008-07-25
I also get an error similar to this, although mine is in english. It happened not long after I tried adding a program in KDE (I use gnome) now the gnome daemon has problems. (both installed on the same system)

Normally some (or most) of my panel addons don't load, but lately its just the CPU freq ones (2 of them). they all used to work fine.

If you could help us by even recommending a website it would be greatly appreciated. Ive done some searches but have yet to find anything useful. 

My system also has had very long boots doing some "routine drive checks". It has only happened the last 3 times Ive booted up, so Im not sure if its permanant, and it may or may not be related to the gnome settings daemon.

Edit: If there is a command line you would like me to run, please put it in a code box. If there is a way to log what is happening during (and not long after) login/loading desktop could you also let us know. Thanks again.

---

### Post by globetrotters1 on 2008-07-27
same here, wrote a message in another thread, but basically I get the same problem

I installed Hardy 8.04.1 desktop, added LAMP server (which crashed on me in the MySQL script) and since then I get this problem

---

### Post by rothalem on 2008-07-29
I think I may have an almost temporary fix to this, although a proper, more permanent fix should be written/explained.

I have set my PC to login for me after 10sec. After ubuntu has logged in and gnome loaded, and I have dismissed the error message of the gnome desktop settings daemon having problems, I say logout.

It auto logs back in, in 10sec, and this time the settings daemon works fine and all my bar notification applets seem to load correctly.

Hope this helps.

I will be reading this thread occasionally to see if a more permanent fix is found.

EDIT: About a week ago I stopped getting this error almost entirely, I thought to myself problems that come by themselves leave by themselves. I updated a couple days ago and the problem is back, only more obtrusive this time. Now re-logging Does not fix the problem at all. I am not sure how to work out what is causing it. Any help would be appreciated.

---

