---
title: "Why do things change? (in relation to D.E)"
date: 2011-11-27
forum: Desktop Environments
---

### Post by grimslider75 on 2011-11-27
Whenever I use nautilus my desktop background changes and I can see icons. 

When the computer boots up, I can right click on the background and change it. However, once the background changes when I use nautilus, right-clicking and then choosing "change desktop background" has no effect. 

Is gnome acting up? How can I use xubuntu and nautilus without my background changing?

---

### Post by IWantFroyo on 2011-11-27
In Gnome, Nautilus controls the desktop.

Install gconf-editor (if you don't already have it), and go to apps->nautilus->preferences.
Scroll down and uncheck "show_desktop"

---

### Post by Copper Bezel on 2011-11-27
Or, if you're on 11.10, install dconf-tools instead and navigate to org.gnome.desktop.background in dconf-editor instead.

---

### Post by grimslider75 on 2011-11-27
> **Copper Bezel said:**
> In Gnome, Nautilus controls the desktop.

Install gconf-editor (if you don't already have it), and go to apps->nautilus->preferences.
Scroll down and uncheck "show_desktop"

> **Copper Bezel said:**
> Or, if you're on 11.10, install dconf-tools instead and navigate to org.gnome.desktop.background in dconf-editor instead.


Tried both of these options, but to no avail. What's going on?

[IMG]http://img855.imageshack.us/img855/6011/screenshotat20111127131.png[/IMG]

---

### Post by Sonador on 2011-11-27
Hi, you have 2 other options:

1. To run nautilus use command ```
nautilus --no-desktop
``` you should know, that clicking on icons on desktop (xfdesktop) will still run thunar (not nautilus)

2. Let nautilus manage your desktop and change background image in dconf-editor 
[http://ubuntuforums.org/showthread.php?p=11362691#post11362691](http://ubuntuforums.org/showthread.php?p=11362691#post11362691)

---

### Post by grimslider75 on 2011-11-27
> **Sonador said:**
> Hi, you have 2 other options:

1. To run nautilus use command ```
nautilus --no-desktop
``` you should know, that clicking on icons on desktop (xfdesktop) will still run thunar (not nautilus)

2. Let nautilus manage your desktop and change background image in dconf-editor 
[http://ubuntuforums.org/showthread.php?p=11362691#post11362691](http://ubuntuforums.org/showthread.php?p=11362691#post11362691)


Solution # 1 works fine, but it is tedious to run that every time I need a file manager.

Without knowledge of what I was doing, In terminal i ran ```
killall xfdesktop
``` and my desktop returned back to normal. For some odd reason, now when I open nautilus, the desktop remains the same. Maybe the dconf and gconf editors are now taking effect. 

Thanks for the suggestions anyways though! :guitar:

---

