---
title: "Lubuntu 11.10 problems (migrating from Gnome 2)"
date: 2012-01-14
forum: Desktop Environments
---

### Post by Nickolai_Leschov on 2012-01-14
Hello,

I've been dissatisfied with the performance of my Ubuntu system (10.04, [generic drivers](http://ubuntuforums.org/showthread.php?t=1893072) => poor desktop performance) and I'm trying Lubuntu 11.10 as an alternative to downgrading Ubuntu.

For now, Lubuntu shows promise, but coming from Gnome 2 (and Windows, earlier), I have the following troubles:

[list]
[*]How do I add programs to the panel?
[*]How do I make my screen configuration stick do dual-monitor layout? I can set resolution alright via "Preferences -> Monitor Settings (Display Settings)", and from there all I need is to run: ```
xrandr --output VGA-0 --left-of DVI-0
``` Where do I put it so that it will run on every startup, preferably before login?
[*]How do I add another keyboard layout? I can't see an option.
[*]How do I change settings in "Preferences -> Keyboard and Mouse -> Keyboard Device Preferences"? (I want to make my keyboard faster than default) Changes don't persist.
[*]How do I fine-tune desktop environment e.g. make menus open faster or disable animation when window is minimized ?
[*]How do I make windows minimize by double-clicking on them ?
[/list]

---

### Post by ajgreeny on 2012-01-14
I can't help with all of those questions, but for the first you need to right click in the application launcher just to the right of the menu button at bottom left, and you can add any program launcher you wish that way.

For all the other queries have a look at [Lubuntu -  Megathread]("http://ubuntuforums.org/showthread.php?t=1844755")

---

### Post by Rodney9 on 2012-01-14
> **Nickolai_Leschov said:**
> Hello,

I've been dissatisfied with the performance of my Ubuntu system (10.04, [generic drivers](http://ubuntuforums.org/showthread.php?t=1893072) => poor desktop performance) and I'm trying Lubuntu 11.10 as an alternative to downgrading Ubuntu.

For now, Lubuntu shows promise, but coming from Gnome 2 (and Windows, earlier), I have the following troubles:

[list]
[*]How do I add programs to the panel?
[*]How do I make my screen configuration stick do dual-monitor layout? I can set resolution alright via "Preferences -> Monitor Settings (Display Settings)", and from there all I need is to run: ```
xrandr --output VGA-0 --left-of DVI-0
``` Where do I put it so that it will run on every startup, preferably before login?
[*]How do I add another keyboard layout? I can't see an option.
[*]How do I change settings in "Preferences -> Keyboard and Mouse -> Keyboard Device Preferences"? (I want to make my keyboard faster than default) Changes don't persist.
[*]How do I fine-tune desktop environment e.g. make menus open faster or disable animation when window is minimized ?
[*]How do I make windows minimize by double-clicking on them ?
[/list]

1. Right click on the panel - Add/Remove Panel Items
2. .config/openbox/autostart.sh
3. Main Menu/Preferences LxKeymap
4. .config/openbox/lubuntu-rc.xml   ***Always make a back-up first !***
5. ?
6. ?


For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by Nickolai_Leschov on 2012-01-14
Thanks for help, **ajgreeny**! Looks obvious, but I expected to be able to add to the panel by right-clicking the program in start menu, like you I could in Ubuntu 8 - 10.

---

### Post by Nickolai_Leschov on 2012-01-14
Thanks for help, **Rodney9**!

2. When I open .config/openbox/autostart.sh it is empty; is it right? The path becomes /home/nb/.config/openbox/ (nb is my user name) I add my line there and reboot; nothing happens.
3. I open LxKeymap, but I can't see how I add another layout (not change the current one).
6. I meant how do I make windows **maximize** and un-maximize when I double-click on the title bar? This is how they behave in Gnome and MS Windows. I got used to it. Can I have this in Lubuntu? For now, I noticed that Chrome behaves like this but LXterm doesn't.

---

### Post by MG&amp;TL on 2012-01-14
IDK if rodney's works, I use .config/lxsession/Lubuntu/autostart

Yes, it's blank.

You can fiddle with the window manager stuff under preferences-> openbox configuration manager.

---

