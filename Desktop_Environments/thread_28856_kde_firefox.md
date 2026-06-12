---
title: "kde firefox"
date: 2005-04-21
forum: Desktop Environments
---

### Post by chen_tso on 2005-04-21
i've installed ubuntu and switched to KDE. however, firefox still seems to be in gnome interface. how do i change it to kde interface? 

i've noticed a lot of system labor with gnome in my pentium celeron, that's why i want to switch it to kde. 

thanks.

pete.

---

### Post by chen_tso on 2005-04-21
nvm. just saw a post....

---

### Post by infornography on 2005-04-25
Any chance of a link? I can't find the thread my self. If it's possible to install Firefox without gtk  I would be very happy about it.

---

### Post by Firetech on 2005-04-25
[http://www.kde-look.org/content/show.php?content=11442](http://www.kde-look.org/content/show.php?content=11442)
The "reverse buttons" version fits KDE perfectly, if you run the plastik style. The default (lipstik) is based on plastik, so it's not much of a problem...

---

### Post by SGC on 2005-04-25
The following package uses KDE theme for GTK+ based application:
[http://packages.ubuntu.com/hoary/kde/gtk2-engines-gtk-qt](http://packages.ubuntu.com/hoary/kde/gtk2-engines-gtk-qt)

After installing it, go to:
Control center > appearance and themes > GTK styles and fonts

And choose:
Use my KDE style in GTK application

---

### Post by Seth on 2005-04-25
[QUOTE=SGC]The following package use KDE theme for GTK+ based application:
[http://packages.ubuntu.com/hoary/kde/gtk2-engines-gtk-qt](http://packages.ubuntu.com/hoary/kde/gtk2-engines-gtk-qt)

After installing it, go to:
Control center > appearance and themes > GTK styles and fonts

And choose:
Use my KDE style in GTK application[/QUOTE]
 Actually, select "Use a Different Theme" and choose Qt. Then you can use a special KDE theme (the instructions above only work if you use the default).

---

### Post by SGC on 2005-04-25
Seth, 
If you choose "Use a Different Theme" then you are just changing the gtk theme

---

### Post by Firetech on 2005-04-26
Ehm? The gtk-qt-engine doesn't work for Firefox, because Firefox has it's own themes.

---

