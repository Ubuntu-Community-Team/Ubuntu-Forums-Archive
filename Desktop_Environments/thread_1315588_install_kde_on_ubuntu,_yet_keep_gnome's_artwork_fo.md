---
title: "install kde on ubuntu, yet keep gnome's artwork for shutdown etc"
date: 2009-11-05
forum: Desktop Environments
---

### Post by chriskin on 2009-11-05
every time i installed kde on my gnome-based ubuntu, kde forced its artwork on my installation, and then i had to see the kubuntu sign every time i shut down ubuntu, etc

which package do i have to reinstall to get the ubuntu artwork back after installing kde?

---

### Post by mrboojive on 2009-11-05
The Ubuntu usplash artwork is in usplash-theme-ubuntu. If you just reinstall that or do```
sudo dpkg-reconfigure usplash-theme-ubuntu
``` it should go back to the Ubuntu splash. If that doesn't work, you might also try removing the Kubuntu usplash artwork package kubuntu-artwork-usplash.

---

### Post by chriskin on 2009-11-05
i remove the kubuntu artwork and all is ok

can you tell me how to make gnome the default wm?
i want kde to be around but gnome is closer to my taste, i would prefer it to log into gnome by default

i'm searching right now for a solution, if i find one before i get an answer, i'll tag the thread as solved :)

---

### Post by mrboojive on 2009-11-05
Are you using GDM to log in? I'm not too familiar with the new GDM, but making Gnome your default should be somewhere in the options on the login screen.

---

### Post by chriskin on 2009-11-05
> **mrboojive said:**
> Are you using GDM to log in? I'm not too familiar with the new GDM, but making Gnome your default should be somewhere in the options on the login screen.

it is, but every time i log into kde, even though gnome is the default one, kde takes it's place until i log into gnome again

it's like it's at "last windows manager used" instead of "gnome = default"

I'll try searching for a long-term solution (or just bear with it)

google brought only another thread that has shown the same problem :S

---

### Post by mrboojive on 2009-11-05
GDM was just rewritten from scratch for Karmic. That might be a bug in GDM.

---

