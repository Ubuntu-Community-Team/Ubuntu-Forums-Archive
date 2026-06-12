---
title: "How to get Non KDE applications to QT4 theming in KDE4 ?"
date: 2008-07-19
forum: Desktop Environments
---

### Post by praveengarlapati on 2008-07-19
I am on Kubuntu Intrepid and don't like the look of the applications Firefox, Thunderbird, GIMP etc..

i.e basically the Non KDE applications. They use different sizes for the menus and don't blend into the desktop.

Is there any way to get these applications look better ?

Note: I have tried to install gtk-kde4 from [http://www.kde-apps.org/content/show.php/gtk-kde4?content=74689&PHPSESSID=81bab81d7c53e374bfa72fc4e60a0132](http://www.kde-apps.org/content/show.php/gtk-kde4?content=74689&PHPSESSID=81bab81d7c53e374bfa72fc4e60a0132) but there are just too many dependencies and I couldn't get it to work.

So if there is any other easy way please do let me know.

---

### Post by benerivo on 2008-07-19
You could try installing the gtk-qt-engine-kde4 package from the repositories using```
sudo apt-get install gtk-qt-engine-kde4
```

The only other alternative is to find a gtk2 theme that matches kde4 and install that. There is one available from [gnome-looks]("http://www.gnome-look.org/") called oxygen accurate, that matches with the default kde4 style.

---

### Post by praveengarlapati on 2008-07-22
> **benerivo said:**
> You could try installing the gtk-qt-engine-kde4 package from the repositories using```
sudo apt-get install gtk-qt-engine-kde4
```


I did try that but cannot see the option in system settings to set the style for gtk applications.

---

