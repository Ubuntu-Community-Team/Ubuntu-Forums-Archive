---
title: "I cant get gtk2 apps to use a theme."
date: 2011-12-16
forum: Desktop Environments
---

### Post by xplus93 on 2011-12-16
I'm on 11.10 and I want to use Elegant Brit GTK3 and GTK2 theme and the Google Gnome shell theme. So far I've been able to get the Gnome shell and GTK3 themes working, but my GTK2 apps look absolutely horrible. I originally tried using just the Elegant Brit GTK3 theme and that didn't work, so I tried copying the gtk2 folder into the Elegant Brit theme folder in /Usr/Share/Themes, that didn't work either. I'm using Advanced Setting for setting themes, is there anything i'm doing wrong or didn't do?

---

### Post by xplus93 on 2011-12-17
Bump, please can somebody give me a bit of info on this, i just got back to using ubuntu after getting nvidia optimus to work and im very new to gnome 3

---

### Post by VCoolio on 2011-12-17
Put the theme in either /usr/share/themes or ~/.themes, and create or edit the file ~/.gtkrc-2.0 so it contains this line:```
gtk-theme-name="Elegant Brit"
``` Check if it needs to be Elegant Brit or Elegant_Brit. If it still doesn't work, launch the gtk2 app from a terminal and check for useful output.

---

### Post by xplus93 on 2011-12-18
I've been able to use gtk2/3 combined themes before, now that you say something about the theme name maybe thats the problem, maybe they are named differently, how would I check for and fix this. I think that might be whats happening Its looking for the gtk2 parts of the theme but cant find them because it thinks they are for a different theme

---

### Post by VCoolio on 2011-12-18
No, the name is specified by the index.theme file inside the theme folder; if that folder contains a gtk-2.0 and a gtk-3.0 folder the theme name is the same.

---

