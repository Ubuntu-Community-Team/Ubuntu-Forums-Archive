---
title: "Qt4 styles without KDE"
date: 2007-05-27
forum: Desktop Environments
---

### Post by antek on 2007-05-27
Hey. I've recently found that there is a possibility to write Java apps using Qt (with Trolltech's Jambi project). The bad part of this that Jambi is based on Qt4, and my KDE is based on Qt3, so I can't change the windows styles to the style that I have on Qt3 (or even any other style). Can anyone tell me how to do it in Qt4? Are there any Qt configuration tools that can be used without using KDE's kcontrol? (Like there is a gtk-related tool, gtk-chtheme, which allows you to change gtk's theme without having gnome/xfce installed).

Right now all the apps are using Motif style and have ugly big fonts. I can force the application to use f.e. cleanlooks theme by using "-style cleanlooks" command line option, but I would like the applications to automatically detect what are the global style settings and use this settings.

Thanks for any help.

---

### Post by antek on 2007-05-27
OK, I've figured it out. I had to install qt4-config package and run qtconfig-qt4 application. It gave me a list of styles I can use and everything is working as it should :)

---

