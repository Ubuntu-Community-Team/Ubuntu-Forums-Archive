---
title: "Metacity vs. Compiz vs. Emerald"
date: 2009-03-23
forum: Desktop Environments
---

### Post by tonyW303 on 2009-03-23
I'm running Ubuntu 8.10 i386 (GNOME) on an AMD Athlon processor (I don't know if that matters). I'm new to Ubuntu. I'm not quite sure but I think Metacity is the default and pre-installed window manager for Ubuntu. I installed Emerald and then Compiz. I think the settings in all three window managers are clashing. I want Compiz to be the main (and preferably only one) window manager. Also, I want it to be the window manager that boots (I currently have to do "compiz --replace" in the run window or terminal). Advice? Help? Thanx!

---

### Post by overdrank on 2009-03-23
Hi and you can add the command to sessions under system, preference. This will allow it on start up. You may want to look at the FAQ link in my signature. :)

---

### Post by Therion on 2009-03-23
You've gone to System, Preferences, Appearance, Visual Effects tab and clicked one of the buttons for "Normal" or "Extra", right?  

And the effects do not "stick" after rebooting?

---

### Post by superbenny on 2009-03-23
> **tonyW303 said:**
> I'm running Ubuntu 8.10 i386 (GNOME) on an AMD Athlon processor (I don't know if that matters). I'm new to Ubuntu. I'm not quite sure but I think Metacity is the default and pre-installed window manager for Ubuntu. I installed Emerald and then Compiz. I think the settings in all three window managers are clashing. I want Compiz to be the main (and preferably only one) window manager. Also, I want it to be the window manager that boots (I currently have to do "compiz --replace" in the run window or terminal). Advice? Help? Thanx!

ok first thing you need to do is add the command ```
compiz --replace
``` to the sessions menu under system>preferences. name it compiz. while in there, if you have a command called Window Manager (it will probably be at the bottom, and the command should be gnome-wm), remove it. it will start after compiz and override it, so you dont want that.
now, if you havent installed ccsm, install it now. you can do that via synaptic, or the command: 
```
sudo apt-get install ccsm
```

then, open ccsm via the run dialogue box (alt+F2) and open up the window decorations setting, and change the command to emerald.

then use the emerald dialogue box to install/choose your theme (you can download them from gnome-look.org)

if all went well, you can restart your computer (or ctrl+alt+bkspc) and it should all work fine.

if compiz is working, but not emerald, add the command
```
emerald --replace
```, and call it emerald. if you named the compiz command compiz, by alphabetical order, it will cause emerald to start after compiz, which you want.

---

### Post by tonyW303 on 2009-03-23
AWESOME! thanx man! =D>

---

### Post by superbenny on 2009-03-23
> **tonyW303 said:**
> AWESOME! thanx man! =D>

no problem! let me know if that works out for you.

---

