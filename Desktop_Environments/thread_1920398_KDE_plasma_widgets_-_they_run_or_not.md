---
title: "KDE plasma widgets - they run or not ?"
date: 2012-02-04
forum: Desktop Environments
---

### Post by Krasus on 2012-02-04
Hi, 

I have a little question about KDE. I was always playing with gnome or xfce and lxde desktops but now I try Kubuntu. 
Now here is the case - I arrange my widgets in KDE and then changed numer of my desktop to 4 and all my widgets and wallpaper disapear :< so I started to rearange my desktops again. When i try to add a new widget for example weather it says that it s allready runnig (but I can add it to the screen) but it is not on the screen :< it s a KDE bug or this widget is really runnig somewhere ? If it is a bug that s ok just need to know :)

It s look like this - its "working" section when u choose what widgets u like to add. 
[http://imageshack.us/f/855/problemory.png/](http://imageshack.us/f/855/problemory.png/)
Using Kubuntu 11.10

Sry, for my bad english.

---

### Post by XeMattress on 2012-02-05
It could be that you activated the option of different widgets on every desktop. On my Kubntu 11.04 Natty it is found in
System Settings -> Workspace Behavior -> Virtual Desktops -> Desktops[tab] -> 'Different widgets for each desktop'.
You will have to deactivate the checkbox in order to get the same widgets on every desktop.
I don't know if it works in your case, but you could try it out.

---

### Post by Krasus on 2012-02-05
Thx for the suggestion. I want to have different widgets on every desktop and I have this. 
I have widgets only on one desktop and I want it to stay this way. The main issue is that the indicator when u choose widgets show that for example weather widget is working but it s not true :< (or mb it is working in background or smth like that ? )

---

### Post by XeMattress on 2012-02-05
It could be (just a thought) that inadvertedly you put the weather widget inside a region of the plasma desktop like the taskbar, the system tray or some other container like that.

You can close widgets only when they are unlocked, which you can select by clicking on the menu which should be situated in the upper right corner of your desktop.

If you can't find all your weather widgets to close them: from some tests I have run it seems to me that the configuration file for the active plasma widgets is situated in
```
~/.kde/share/config/plasma-desktop-appletsrc
```For example, my own configuration file contains the following text for a working weather widget:
```
[Containments][1][Applets][86]
geometry=266,580,277,192
immutability=1
plugin=weather
zvalue=70

[Containments][1][Applets][86][Configuration]
Share=false
pressureUnit=5008
source=XXXXXXXXXXXXXXXXXX
speedUnit=9000
temperatureUnit=6001
updateInterval=30
visibilityUnit=2007
```You could try to delete all configuration sections of weather applets (for each applet they seem to come at least twice). As a general safety rule: **Be *careful* when modifying your configuration files!** At least make a backup copy of it, which you are able to restore afterwards even from CLI (command line interface), and be sure you know how to do it.

When you feel your problem is solved, mark the thread as solved.

---

### Post by Krasus on 2012-02-06
Ok thx ! 
editing this file works now the widgets are marked as not working.

It must be used with sudo, then log out and log in again.

---

