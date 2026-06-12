---
title: "Emerald Help"
date: 2010-03-11
forum: Desktop Environments
---

### Post by yomnym on 2010-03-11
Ive been trying to get something going that looks clear, like glass windows, borders all the things, somewhat like Win7.  I have installed Emerald but i cant seem to get it right.  When i download a theme from gnome-look.org or any other place i place it on my themes folder or just import it when Emerald, nothing happens.  I tried adding a start up application with the command ```
emerald --replace
``` but that did absolutely nothing.  When i open terminal and enter emerald --replace i get some what a hint of the theme but not all of it, just the terminal window i want the status bar, the top status bar, everything..  I need all the help the community could offer to get some themes working here.  Thanks a lot for your help.

---

### Post by hhh on 2010-03-11
For the status bars, I think you mean the Gnome panels, right click on each panel>Background>Solid Color>slide the slider all the way to "transparent".

HTH

-edit- For a transparent background on your terminal, it's Edit>Profile Preferences>Background>Transparent Background and again with the slider.

---

### Post by yomnym on 2010-03-11
Sweet, learned something new.  So then what do the themes do exactly, customize the windows?  Thanks for your help, now i hope someone else can chime in about the emerald auto starting.

---

### Post by yomnym on 2010-03-11
Well i learnt how to make emerald work.  First you need to have Compiz working so open Compiz>Effects>Windows Decorations then under the command space enter 
```
emerald --replace
```, also make sure that "decoration windows" = any
and "shadow windows" = any as well and this should enable you to run your themes.

---

### Post by dbowlin17 on 2010-03-12
hey, so i tried doing this, but had the same issue still...

---

### Post by yomnym on 2010-03-15
I'm assuming you got Emerald with a theme installed in it, Compiz manager installed and "window decoration" enabled?  I'm not really so great at Ubuntu, and most of the things that worked for others didn't work for me.  I found a few help threads around google which may have contributed to my success.  Try [this]("https://help.ubuntu.com/community/CompositeManager/CompizFusion") or [this]("http://ubuntuforums.org/showthread.php?t=495997").  Best of luck.

---

