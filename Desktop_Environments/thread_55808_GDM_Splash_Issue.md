---
title: "GDM Splash Issue"
date: 2005-08-10
forum: Desktop Environments
---

### Post by tzutolin on 2005-08-10
Hello, everyone

I did a fresh install today. When i logged into gnome, the splash screen won't disappear automatically, and i have to click on it or start another application to hide it. Can anyone help me to solve this problem? Thank you very much!  :)   :)   :) 

Oh, by the way, i'm using the "server" install mode. And then "apt-get install x-window-system-core gnome-core gdm xscreensaver".

---

### Post by tzutolin on 2005-08-10
Sorry guys :)

I think i found the solution, here it is :)
[B]
sudo apt-get install linux-686-smp sysv-rc-conf nvidia-glx esound x-window-system-core gnome-core gnome-cups-manager gnome-media xscreensaver gdm[/B]

Thanks for watching this thread.

---

