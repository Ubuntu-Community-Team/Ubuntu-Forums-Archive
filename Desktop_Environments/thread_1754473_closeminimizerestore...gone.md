---
title: "close/minimize/restore...gone"
date: 2011-05-10
forum: Desktop Environments
---

### Post by SharkBreeder on 2011-05-10
The close/minimize/restore bar vanished ever since upgrading to 11.04. Does anyone know how I can get it back?

---

### Post by FuePi on 2011-05-10
I assume you're using the Unity GUI. 
You can find the title/menu bar of a window in the Unity panel at the top of the screen.
If you move your mouse to the panel, it shows the title menu of the current window. 
There are also the close/minimize/maximize buttons (all the way to the left).

---

### Post by SharkBreeder on 2011-05-10
Unity is disabled--I'm using gnome.

---

### Post by Grenage on 2011-05-10
> **SharkBreeder said:**
> Unity is disabled--I'm using gnome.

Try this from a terminal:

export DISPLAY=:0
metacity --replace

If you can't access a terminal, just use Ctrl-Alt-F1 (use Ctrl-Alt-F8 to get back).

---

### Post by SharkBreeder on 2011-05-10
Installing gnome 3 helped fix the problem. Thanks.

---

### Post by Krytarik on 2011-05-10
For anyone who don't want to apply the OP's Gnome 3 fix ;-) , make sure Compiz' "Window Decoration" plugin is enabled in "CompizConfig Settings Manager", and the package "compiz-gnome" (respectively "compiz") is installed.

Greetings.

---

### Post by SharkBreeder on 2011-05-10
@Krytarik

I'll make sure I get that done. Thanks.

---

