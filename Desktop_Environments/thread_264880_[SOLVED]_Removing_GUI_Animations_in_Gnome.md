---
title: "[SOLVED] Removing GUI Animations in Gnome"
date: 2006-09-25
forum: Desktop Environments
---

### Post by altonbr on 2006-09-25
I installed Kubuntu on my sisters (old) computer because she liked "the pretty colours" although I now know it was a mistake since KDE is synonymous with needless animations. But I easily corrected this by going through System Settings and disabling some animations and lighting effects.

My question is how to do this is Gnome (Ubuntu). When I use Windows, I'm a big fan of the Windows 98 (or Classic Windows) theme and turning off all the animations. It is all I need for a GUI and find it sort of slick. Are there any options in Ubuntu that are as verbose in changes as the ones in Kubuntu? Or would this require manually editing some config files?

I'm sure this has been asked before, but I wasn't sure was were the correct keywords to search for. Any link will be much appreciated. Thank you.

---

### Post by ayoli on 2006-09-25
have a look in gconf-editor (which is in menu "system tools", or hit ALT + F2 and enter gconf-editor in the run dialog).
for example in this path in gconf-editor, /apps/panel/toplevels/top_panel_screen0 , you have a setting to enable/disable animations (see screenshot). 
btw, original gnome has not many animations features IMO. So you may describe more what animations you want to disable.

---

### Post by altonbr on 2006-09-26
Yes, you're right, Gnome doesn't have many animations at all. But if I were trying to make my theme as lean as possible (comparable to the Windows 98 theme)... what suggestions would you have?

---

### Post by altonbr on 2006-12-15
So for speeding up GNOME (Ubuntu), go to the Terminal (Applications > Accessories Terminal)
and execute:

> gconf-editor

then to speed it up, go to:
> apps >> panel >> toplevel >> top_panel_screen0
and change "enable_animations" to "false" (uncheck)

The new one I found is:
> apps >> metacity >> general
and change "reduced_resources" to "true" (check)

Hope this helps someone :)

---

### Post by mcduck on 2006-12-15
In gconf-editor there is also a 'master' key top turn off all animations, including those in metacity, nautilus and panels.

it's desktop/gnome/interface/enable_animations

---

