---
title: "Use other WM"
date: 2005-04-25
forum: Desktop Environments
---

### Post by defkewl on 2005-04-25
How do I change the default desktop, I want to use a lighter WM than Gnome.

Thnx for the help

---

### Post by lao_V on 2005-04-25
Very simple, just install it from synaptic..xfce, enligtenment, fvwm..whatever you please!

---

### Post by defkewl on 2005-04-25
[QUOTE=lao_V]Very simple, just install it from synaptic..xfce, enligtenment, fvwm..whatever you please![/QUOTE]

Yes I know. But when I type startx from the command line, it directly goes to Gnome. I want to change it other than Gnome :D

---

### Post by tread on 2005-04-25
Change the .xinitrc file in your home directory. If there isn't one, create it.
Doesnt have to be fancy, just type in the name of the window manager, e.g., 

exec enlightenment

(If you use gdm, you can click on session and change the windowmanager to any other that you may have installed, instead of fiddling around with the .xinitrc file)

---

