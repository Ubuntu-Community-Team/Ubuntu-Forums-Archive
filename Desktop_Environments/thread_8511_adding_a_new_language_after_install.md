---
title: "adding a new language after install??"
date: 2004-12-18
forum: Desktop Environments
---

### Post by amandla on 2004-12-18
I installed worty with english as the default language. However, i wish to add spanish and portugese as a login option. Anyone know how i may go about doing this??


Cheers,
amandla

---

### Post by burlap on 2004-12-19
You have to run 
```
sudo dpkg-reconfigure locales
```
and add new languages there (set default if necessary). After reboot you should have them in gdm language menu.

---

### Post by amandla on 2004-12-20
Thanks!!! Worked like a charm! :D

---

### Post by alainhenry on 2004-12-20
I tried this tip, which allowed me to add a locale (French Belgian), but the keyboard layout remains qwerty, while I have an azerty layout.  How could I chnage that in gdm ?
Thanks
Alain

---

### Post by burlap on 2004-12-20
I don't think you can change keyboard layout in gdm. But: you can do it via Computer -> Desktop preferences -> Keyboard and you can also add keyboard applet to gnome panel.

---

### Post by alainhenry on 2004-12-21
I can, and have, changed the keyboard layout with Computer > Desktop preferences > Keyboard.  So all programs recognise the correct keyboard layout.  And you can swicth from one to the other, as long as you stay within Gnome.  But during login (§i.e. before starting gnome, in a way) , whatever I did, I am stuck with the qwerty layout.  

I did an install in French some time ago, and the login used the azerty layout.  Now I re-installed in English, but can't tell the login manager that I want to rad inputs from an azerty keyboard.  I imagine I could do this without re-installing the whole distro.  

Alain

---

