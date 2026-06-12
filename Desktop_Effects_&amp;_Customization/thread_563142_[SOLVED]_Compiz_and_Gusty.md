---
title: "[SOLVED] Compiz and Gusty?"
date: 2007-09-29
forum: Desktop Effects &amp; Customization
---

### Post by slughappy1 on 2007-09-29
So I have just a very simple question. I just installed the beta of Gusty. I already love it. I have an intel 915 integrated graphics card which gave me some problems in Feisty, but it works and I didn't have to do ANYTHING. Anyway my question is does anyone know where the compiz settings manager is? I noticed in synaptic that it has all of the compiz packages installed, except the development packages. Maybe I am just blind, but I can't find where to change anything about compiz.

---

### Post by CaptainInsaneO on 2007-09-29
It *should* be under System>Preferences>Compizconfig

If you can't find it under there, type ccsm into a console. It will let you go from there.

---

### Post by slughappy1 on 2007-09-29
See that is where I first looked. But for some reason it isn't there. I will try the ccsm thing next

---

### Post by Rupertronco on 2007-09-29
> **slughappy1 said:**
> See that is where I first looked. But for some reason it isn't there. I will try the ccsm thing next

Even if you do get it to your menu eventually, pressing Alt+F2 and typing "ccsm" is loads faster than navigating menus. 

I frequently change my compiz settings, if I have a terminal open I'll just run it from there, but just bringing up the run command and typing ccsm is easily the best way to go.

---

### Post by master_kernel on 2007-09-29
Open a terminal and enter:
```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by michaelzap on 2007-09-29
I read in a Gutsy overview that you have to install the Compiz settings manager separately. By default they just give you three generic options (i.e., off, some effects, lots of effects). Look for the settings manager in Synaptic (or check the Compiz Fusion forums).

---

