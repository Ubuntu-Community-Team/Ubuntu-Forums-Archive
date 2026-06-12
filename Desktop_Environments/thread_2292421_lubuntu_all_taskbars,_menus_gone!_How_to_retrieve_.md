---
title: "lubuntu: all taskbars, menus gone! How to retrieve them?"
date: 2015-08-27
forum: Desktop Environments
---

### Post by siggi2 on 2015-08-27
Hi,

when I boot into my Lubuntu 14.04.2 LTS today, it starts as usual, i.e., the bluish Lubuntu screen, the mouse pointer, but that is it! No menu, no taskbar, no n, otification, no date, no "nothing". I can get into <Ctrl>+<Alt>+<F5> textmode, login, "sudo reboot" but it does not help.

What could I do to get my working Lubuntu back?

Thanks,

siggi

---

### Post by Rex Bouwense on 2015-08-27
Sounds like you booted into OpenBox.  Right click on the screen and see if you get a small menu.  If you do reboot and when you get to the log in screen choose Lubuntu from the drop down menu from the first icon.

---

### Post by siggi2 on 2015-08-28
Thanks, Rex,

but there is no right-klick-menu, and I start from Lubuntu as I always do. I can start from OpenBox. It looks similar, empty destop, but there is a right-klick-menu; it does not help either.

_Could I not work from text mode to make the menu and the indicator bar visible?_

siggi

---

### Post by CantankRus on 2015-08-28
From tty 5 login and run...
```
export DISPLAY=":0.0"
```
then startup what you want in your xsession...
eg
```
lxpanel
lxterminal
```
Ctrl+Alt+F7 to get back to your desktop.

If your desktop is showing desktop icons you can also set an lxterminal desktop shortcut.
```
cp /usr/share/applications/lxterminal.desktop ~/Desktop
chmod +x ~/Desktop/lxterminal.desktop
```



If you think you may have inadvertently removed something critical to Lubuntu, try running
```
sudo apt-get update 
sudo apt-get install lubuntu-desktop
```

---

### Post by siggi2 on 2015-08-31
> **CantankRus said:**
> From tty 5 login and run...
```
export DISPLAY=":0.0"
```
then startup what you want in your xsession...
I got an lx desktop back with this command, thanks, but the most important panel item, the Lubuntu icon to the far left "housing" all important menu items, was missing. I could not retrieve it, neither could I add important menu items to the panel (as I was able to with a functioning Lubuntu)

> If you think you may have inadvertently removed something critical to Lubuntu, try running
```
sudo apt-get update 
sudo apt-get install lubuntu-desktop
```
It restored a bit more, but all panel items had the same appearance, i.e., looking like small monitors.

And somewhere in the process there was something like "...X11 initializaiton failed...".

Frustrated, I gave up, and deinstalled Lubuntu.

However, since I plan to replace Xubuntu on my ancient PC with Lubuntu when the next LTS version is out, what could have caused this strange disappearance of the Lubuntu desktop? Any guesses welcome!

Thanks,

siggi

---

