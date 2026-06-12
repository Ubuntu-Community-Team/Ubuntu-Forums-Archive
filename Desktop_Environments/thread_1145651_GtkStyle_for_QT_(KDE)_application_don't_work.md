---
title: "GtkStyle for QT (KDE) application don't work"
date: 2009-05-01
forum: Desktop Environments
---

### Post by samoul on 2009-05-01
Hy, i'm on 9.04 and i'm trying to apply the GTK+ theme from Troll Tech to KDE applications. I used to work very easily on 8.10 but i just can't make it work. I select the GTK+ theme in Qt 4 Settings (System/Preference/Qt 4 settings) but all my KDE application keep their original look under gnome. I've also try to compile and install the SVN directly from Troll Tech labs ([http://labs.trolltech.com/page/Projects/Styles/GtkStyle](http://labs.trolltech.com/page/Projects/Styles/GtkStyle)). I can install it but when i select the theme in Qt 4 Settings nothing change! Well if you have any idea...

Thanks!

---

### Post by samoul on 2009-05-02
If you are interested to try the latest version of QGtkStyle from Troll Tech SVN here is how:

*  What you need to compile...
```
sudo apt-get install subversion qt4-qtconfig libqt4-dev libgtk2.0-dev libgtkextra-x11-2.0-dev checkinstall
```

* Get the source...
```
svn co svn://labs.trolltech.com/svn/styles/gtkstyle
```

* Prepare and compile... 
```
cd gtkstyle/
qmake
make
sudo checkinstall 

```

As I mentioned before, the installation goes perfect but nothing append when I switch QT Theme is Qt 4 Settings...

---

### Post by samoul on 2009-05-02
Cool i've come up with a solution!

* Install systemsettings package
* Install kdeartwork package

That's all you need to select GTK+ theme for KDE application. Once both of thoses package (and dependency) are installed you will have the kde System Settings application under Application/System Tool/System Settings. Go to Appearence and choose GTK+ as Style, humain icon set as icon theme and ajust you font rendering settings so it match thoses in Gnome Appearance settings.. Well it's not rocket science ... you just need systemsettings and kdeartwork package! Enjoy.

By the way it's still a bug user should not have to install thoses packages and do the work manually it should be automatic, if a KDE application is installed under gnome then GTK+ theme should be enable...

---

