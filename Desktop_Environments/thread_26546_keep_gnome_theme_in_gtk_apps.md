---
title: "keep gnome theme in gtk apps"
date: 2005-04-13
forum: Desktop Environments
---

### Post by doni on 2005-04-13
hi there...

my problem: if i fire up a gnome (gtk) app the theme of it looks ugly and not nice. i can solve that with launching gnome-theme-preferences and it then takes the theme i select there...
but that only stays until i log out.

is there a way to keep that all the time?

gtk apps just suck that way they look now...

thanks
doni

---

### Post by kal_zakath on 2005-04-13
you have to install the package called "gtk2-engines-gtk-qt" : 
```
sudo apt-get install gtk2-engines-gtk-qt
```
or use synaptic/ksynaptic to install it.

Then go to :

Kde Control center --> Appearance & Themes --> GTK Styles and Fonts

and either choose tu use KDE style in gtk apps or use a gtk theme (i.e. : you can use gtk2-engines-clearlooks, if it isn't installed, just install it and you will be able to choose it in the drop down list of avariable gtk themes)

---

