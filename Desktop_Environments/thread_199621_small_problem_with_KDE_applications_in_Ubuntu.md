---
title: "small problem with KDE applications in Ubuntu"
date: 2006-06-19
forum: Desktop Environments
---

### Post by freewind on 2006-06-19
Hello All!
I'm sorry for my english.
I have a small problem with KDE application. This application written in QT and require libqt3-mt for it's work. I use it for my work in Ubuntu 6.06. Then this application work, I see that it have different window decoration (like Win98 style) and different font in menu with comparision with my Gnome theme settings. How I can force this application to use my Gnome theme settings and fonts.

Thank you.

---

### Post by ayoli on 2006-06-19
qt apps can't use gtk (gnome) themes, you can tweak your qt/kde style with kcontrol to have it closer to your gtk/gnome theme, that's all...
other way is using gtk2-engines-gtk-qt with allow to apply a kde theme to gtk/gnome apps.
cheers.

---

### Post by metafile on 2006-06-19
Afaik it`s impossible to make Qt apps look exactly as GTK ones, but I think [this](http://ubuntuforums.org/archive/index.php/t-76633.html) is what you`re looking for.

---

### Post by freewind on 2006-06-19
thank you

---

