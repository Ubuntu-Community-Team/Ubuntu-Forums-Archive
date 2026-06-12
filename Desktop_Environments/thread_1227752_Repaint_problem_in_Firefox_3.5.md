---
title: "Repaint problem in Firefox 3.5"
date: 2009-07-31
forum: Desktop Environments
---

### Post by tayran on 2009-07-31
Hi,

In Firefox 3.5.1 most HTML form components like radio buttons, drop downs etc. are not shown properly when i scroll through the page so that the components are invisible and then visible again. I have to move the mouse over them to make them appear. Otherwise they are only partially drawn.

I am using Kubuntu 9.04 with KDE 4.2.2 and 
gtk-qt-engine-kde4 package for gnome applications. Also i have set in the System Settings that KDE should use KDE style in GTK apps.
My theme is the default theme Oxygen by the way..

---

### Post by Zorael on 2009-07-31
Try telling it to use the *Qtcurve* style in GTK apps instead of your KDE style. I think the packages needed are **kde-style-qtcurve** and **gtk2-engines-qtcurve** - not sure to what extent gtk-qt-engine-kde4 is used anymore?

---

### Post by tayran on 2009-07-31
Thanks that helped me.

But now drop downs are larger with respect to the previous Qt4 version. Anyway i have to get used to this.

---

