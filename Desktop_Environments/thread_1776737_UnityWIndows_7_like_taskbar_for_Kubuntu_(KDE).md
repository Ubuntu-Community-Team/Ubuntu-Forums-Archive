---
title: "Unity/WIndows 7 like taskbar for Kubuntu (KDE)?"
date: 2011-06-06
forum: Desktop Environments
---

### Post by mothergoose729 on 2011-06-06
A simple questions really, I was wondering if Kubuntu had the task bar equivalent of these two apps. What I am looking for specifically is the icon representation of windows rather then text minimizations, with window grouping and organizing, ect. I have cairo installed right now but I don't like it. Its very flashy all the effects are kind of over the top and difficult to tame. An applet would be best, because I have multiple monitors and I would like it if I could run multiple instances of some kind of "dock" like you can in KDE with the vanilla task manager. Anyone know of such a thing?

---

### Post by Frogs Hair on 2011-06-06
The closest thing I know of to the Windows task-bar is Dockbar x and they make a Unity style launcher as well. I don't see a KDE version any where.:(  
[http://www.omgubuntu.co.uk/tag/dockbarx/](http://www.omgubuntu.co.uk/tag/dockbarx/)

---

### Post by Copper Bezel on 2011-06-06
It's of course usable in AWN, but AWN doesn't jive with KDE's network applet, to my knowledge. Otherwise, you could just replace the panel with that.

---

### Post by Zorael on 2011-06-06
There's [Smooth Tasks](http://kde-look.org/content/show.php/Smooth+Tasks?content=101586), package name [**plasma-widget-smooth-tasks**](apt://plasma-widget-smooth-tasks).

The screenshots there aren't helpful but it's like the W7 taskbar. Don't forget to run '**kbuildsycoca4**' after installing the package. Then just unlock widgets, click the cashew on your panel, hit Add Widgets and find Smooth Tasks in there.

---

### Post by Neoxhadowespio on 2011-06-06
Hmmm... I prefer the Gnome because it is faster and a lot more functional. Gnome is in a way closer to Windows 7.

---

### Post by NormanFLinux on 2011-06-06
Smooth Tasks is terrible... you don't even get a decent open window.

I recommend the Fancy Tasks plasmoid... which will provide an OSX-style dock in KDE. Put next to it the Task Manager so you get the right open window when you launch an application from the Fancy Tasks launcher.

---

### Post by luisfpg on 2011-06-08
Smooth tasks is the closest one in appearance, at least, to the W7 launcher.
The main thing I've been looking for is some widget which combines launchers with the task manager (just like W7 or Unity launchers).
The approach KDE has adopted (at least in 4.6, don't know if it's going to change) to add a launcher when the application is not running is terrible.
Ideally, I'd like to see an Unity-like plasmoid (which even supports counters, progress bars and quick lists), but that might be a too distant dream...

---

### Post by Copper Bezel on 2011-06-08
I'd use DockBarX and Avant Window Navigator, then. (I mean, I do, but I'd suggest them under KDE, too.) = ) There's no way to put it *in* the KDE panel, but it has the settings to make it match or coordinate nicely.

```
sudo add-apt-repository ppa:awn-testing/ppa 
sudo add-apt-repository ppa:dockbar-main/ppa
sudo apt-get update
sudo apt-get install avant-window-navigator-trunk dockbarx awn-applet-dockbarx
```

Then just empty out the AWN panel and add DockBarX. If you want it to auto-hide, leave the Launcher / Task Manager applet in AWN but set it to Show Only Launchers and remove the launchers it has.

---

