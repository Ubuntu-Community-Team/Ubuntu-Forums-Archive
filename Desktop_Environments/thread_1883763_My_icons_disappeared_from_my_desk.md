---
title: "My icons disappeared from my desk"
date: 2011-11-19
forum: Desktop Environments
---

### Post by ArielNokia on 2011-11-19
I need help, do not see my desktop icons, or respond by clicking the right mouse button, does not leave the options menu, for example to change the wallpaper.
 If I change my user account, the desktop works fine, the icons are normal and everything works fine, but I lose all the settings I have in my user account.
 If I run "sudo nautilus" in a terminal, the desktop respond, but do not show the icons that are in the "desktop", but I can add new launchers and reset everything goes wrong again.
 Please know that the other applications and panels are working properly, I have Ubuntu 11.10 and Gnome 3.2
 I hope you understand my English and you can help me, I've tried several possible solutions and I can not solve this problem.

 Thank you very much, Ariel from Argentina

---

### Post by Copper Bezel on 2011-11-19
Nautilus isn't managing the desktop, then. There are a couple of ways to change that - through gnome-tweak-tool ("Advanced Settings") or through dconf-editor. 

In Advanced Settings, if you have it installed, make certain that "Have file manager manage the desktop" is enabled in Desktop options.

In dconf-editor, if you have dconf-tools installed, navigate to org > gnome > desktop > background and make certain that the options to draw the background and provide icons are set.

---

### Post by ArielNokia on 2011-11-19
Thank you, thank you very much for your quick response, it worked perfectly, I am very grateful, and I was desperate and did not get any help in the Spanish forum and there was a solution searching with Google, almost 24 hours I was with this problem and not know what to do, had tried reinstalling all, THANK YOU!! :lolflag::lolflag::lolflag:

---

### Post by Copper Bezel on 2011-11-19
Very cool! Just mark the thread as solved (Thread Tools in the upper right.) = D

---

