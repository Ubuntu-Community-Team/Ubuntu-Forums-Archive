---
title: "How do I set the default WM"
date: 2005-07-25
forum: Desktop Environments
---

### Post by musther on 2005-07-25
I've been looking everywhere, how do I set the default window manager?

---

### Post by charlieg on 2005-07-25
In Gnome, bring up the GConf editor (Configuration Editor under Applications -> System Tools) and search for 'manager'.  Near (if not) the top should be '/desktop/gnome/applications/window_manager'.  Edit that to be your preferred wm!

---

### Post by Who on 2005-07-25
If you are using GDM as your display manager (which on my system was the default) then when you choose a different window manager to the one you normally use it asks you whether you want to make it the default, or use it just for one session. That is how I would have done it. If you are using KDM then (in older versions of KDE at least) you can choose which is the default from the right part of kcontrol (the KDE Control Centre) - just use the search or the index tab and use the phrase 'display manager' or 'manager' (I am not at a linux box so I can't get the details - sorry). The choice of whether to use KDM or GDM was given to me as I installed KDM as part of kubuntu. As they were on my sytem KDM gives a blue screen, GDM gives a yellow one.
The gconf thingy will _probably_ only work if you are using GDM, which by the fact you needed to ask how to choose a defult I assume you are not. 
Finally, providing you have the root password, you can use the less direct but more friendly version of the solution by using the GDM configurator - which (again, in other flavours on older versions, so it may have moved) can be found by choosing actions from GDM and then 'Configure GDM' or something similar.

Sorry, this is quite vague, but things should be quite apparent.

Who

---

### Post by charlieg on 2005-07-25
There's a different between default WM for Gnome and default DE/WM.  I assumed the OP meant the former (which you change through GConf so that Gnome uses your favourite WM instead of Metacity) whereas you refer to the latter, which is controlled (as you say) through GDM (or KDM).

---

