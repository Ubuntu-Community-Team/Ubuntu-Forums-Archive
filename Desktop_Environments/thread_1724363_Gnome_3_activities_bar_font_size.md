---
title: "Gnome 3: activities bar font size"
date: 2011-04-08
forum: Desktop Environments
---

### Post by _0R10N on 2011-04-08
Hi everybody! Yesterday I installed Gnome 3 and the first thing I noticed is a new bar, the activities bar, and the new notifications system. I've looked around, with no luck, trying to change the size of the font of this bar (and dialogs). So I decided to ask my friends on ubuntuforums if someone knows how to do it.

Thanks in advance! 

Kind regards!

---

### Post by morgue on 2011-05-03
gnome-tweak-tool might have what you are looking for, it's the only way I've found to change settings in gnome 3 so far.

---

### Post by sgaap on 2011-05-12
I dont think that it's doable with gnome-tweak-tool (yet)

If you use the gnome-shell theme extension you can edit the theme you use manually in **.themes/<theme name>/gnome-shell/gnome-shell.css** or if you just got a stock gnome 3 install in **/usr/share/gnome-shell/theme/gnome-shell.css**

Just search for "**.panel-button**" and change the font-size (if its not there just add "**font-size: 12px;**" within the brackets of that class, ofc: if you want a different font size just change 12 to whatever you feel like.

---

### Post by VRathor on 2013-04-07
hey there,
I had the same problem with the font size of Activities bar + my 'system-monitor' shell extension was replacing the clock in the middle. Got rid of both!!
For font size, sgapp's trick worked (thanks @sgaap).
For the clock in the middle, i found an option in the shell-extension itself which says 'Move the clock' (is that so simple!!!). Just uncheck it & there you go. To get to shell-extension's option, go to [https://extensions.gnome.org/local/](https://extensions.gnome.org/local/) and in front of 'system-montior' extention among other, there will be an option saying 'configure'. That's it.

---

### Post by oldos2er on 2013-04-07
Old thread closed.

---

