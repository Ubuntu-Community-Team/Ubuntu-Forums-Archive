---
title: "Ubuntu 6.10 with KDE"
date: 2007-04-12
forum: Desktop Environments
---

### Post by super.rad on 2007-04-12
I've installed Ubuntu 6.10 on my girlfriends computer, last night i installed KDE desktop to show her by doing
```
sudo aptitude install kde-desktop
```
now she's decided she wants to keep KDE and wants to get rid of GNOME, how do i do this? 
Im guessing to get rid of the desktop i just type into a terminal
```
sudo aptitude remove gnome-desktop
```
but is their a way i can remove all the gnome applications aswell?
Basically i want to get kubuntu 6.10 but without having to uninstall ubuntu and install kubuntu
Thanks

---

### Post by fwojciec on 2007-04-12
This might help: [http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

---

### Post by super.rad on 2007-04-12
thanks, but im still a bit confused, i read that page but what im not sure about is i started out with gnome and then installed the kde desktop, so will typing
```
sudo aptitude remove gnome-desktop
``` 
get rid of the gnome desktop and all the gnome applications aswell?

---

### Post by fwojciec on 2007-04-12
Since you did not install gnome-desktop with aptitude you won't be able to remove it with aptitude.  The other command (the one that lists all the individual apps) should remove the entire gnome environment (desktop and applications) - if this is what you're trying to do.

Alternatively you could just set KDE as the default session and leave Gnome as backup in case something goes wrong with KDE...

---

### Post by super.rad on 2007-04-12
right i've done that and it's all worked fine thanks.
i have another question, as im now running ubuntu with kde desktop do i need to change the repositories to the kubuntu ones? and if i do, where would i find them. Thanks

---

### Post by fwojciec on 2007-04-12
You don't need to change the repositories - they are the same for all desktop environments.

---

