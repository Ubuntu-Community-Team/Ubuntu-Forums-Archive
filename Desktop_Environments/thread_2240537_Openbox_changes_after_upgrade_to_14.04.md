---
title: "Openbox changes after upgrade to 14.04"
date: 2014-08-20
forum: Desktop Environments
---

### Post by cov on 2014-08-20
[ATTACH=CONFIG]255679[/ATTACH]

Since upgrading to 14.04 I have this weird sidebar to the right of the desktop. It doesn't seem to do anything and only the editor icon works. (it starts up Leafpad).

The normal tray is at the bottom.

I can still use the normal tray and the right-click menus, so it's no big deal, but what is the sidebar for and how does it work?

---

### Post by vasa1 on 2014-08-20
That sidebar isn't part of Lubuntu 14.04 when a clean install is done. This seems to be a consequence of upgrading as opposed to doing a clean install. Anyway, if it is indeed a panel created by Lubuntu's lxpanel, if you right-click on a blank space in the sidebar, you should see an option to "delete this panel".

Are you sure it isn't some sort of "dock" or another panel you installed at one time and then forgot about? I doubt changes to Openbox have anything to do with that panel/dock.

---

### Post by cov on 2014-08-21
Yes, it probably is something I tried to install, failed and then forgot about.

It's actually quite cool if I could get it to work; it has a very 'Mac-like' animation.

However, I can't seem to configure it: right-clicking anywhere on the bar doesn't have any effect. The top icon says 'Config', but clicking it, right-clicking it or double-clicking it opens nothing. It just sits there looking at me.

---

### Post by vasa1 on 2014-08-21
You might get a hint by running```
'COLUMNS=150 ps -ef > ~/Desktop/processes.txt'
```just after you log in and then looking at the contents of processes.txt. If you want, you could post the output here between code tags and someone may identify that panel/dock for you and help figure out how to get it going.

---

### Post by vasa1 on 2014-08-21
You could also post the output of **ls ~/.config** and if you have a subdirectory in ~/.config called **autostart** you could post the output of **ls ~/.config/autostart** as well.

---

### Post by vasa1 on 2014-08-21
BTW, is this the same machine which is/was nearly full during upgrading?

---

### Post by cov on 2014-08-21
>COLUMNS=150 ps -ef > ~/Desktop/processes.txt

Cool! it looks as if the sidebar is called **wbar** and it has a man page [sweet]. My systemtray is **stalonetray**. There's probably a conflict that's causing this; I need to investigate and possibly disable one or the other.

> post the output of ls ~/.config/autostart as well.
```
dave@Threepwood:~$ ls .config/autostart/
nm-applet.desktop       xfce4-notes-autostart.desktop
remmina-applet.desktop  xfce4-settings-helper-autostart.desktop
skype.desktop

```
Not too much of interest there...

>BTW, is this the same machine which is/was nearly full during upgrading?

Yes it is.

My python installation seems to be borked [python's incompatibility issues with itself are absolutely insane! IMO, of course - I don't want to start a flame war :) ].
I wouldn't have thought that that would be affecting this... except possibly it may be why the wbar is not responsive.

Dave

---

