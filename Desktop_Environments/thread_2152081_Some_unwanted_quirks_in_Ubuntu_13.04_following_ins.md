---
title: "Some unwanted quirks in Ubuntu 13.04 following installation of Cinnamon"
date: 2013-06-06
forum: Desktop Environments
---

### Post by LMDevlin on 2013-06-06
Hi all, hoping you can help me out with a problem which confuses me.

The other day I installed the Cinnamon desktop environment, alongside Unity. Ever since then I have a few quirks which I would like to be undone and returned to their default behaviour:

1) The dynamic login/lock-screen wallpaper doesn't work any more, by that I mean that whatever I change my desktop background to when logged into Unity, it doesn't change on the login or lock-screen.

2) My lock screen now has a clock on it. I'm pretty sure it didn't have it before.

3) My right click > Change Desktop Background Menu is blank, plus when I click All Settings on that menu it takes it to a different "System Settings" window, which to me looks like Cinnamon's settings window (if I go to the power button in the top-right corner and go to System Settings it is the normal Ubuntu menu).

[IMG]http://i.imgur.com/Tax8xw5l.png[/IMG] [IMG]http://i.imgur.com/MSl3R3ul.png[/IMG]

4) I also have an "Add Desklets" option on my right-click Desktop menu, which I'm sure wasn't there before.

I guess installing Cinnamon has changed some things that I didn't want it to change- short of removing Cinnamon, how can I revert them back to how they were? Would removing Cinnamon even work?

Many thanks for any help in advance.

---

### Post by LMDevlin on 2013-06-26
Sorry to bump, but does anyone have any ideas for this? Did I ask the question wrong, perhaps?

---

### Post by snakeplizzken on 2013-06-26
I use the same setup Ubuntu 13.04 plus Cinnamon 1.8.
The problem I have is that sometimes then I log in the background is totally black.
Then I open Nemo and almost always the background updates correctly.
Maybe it is because I use the Bisigi themes? They are a bit old but very good looking.

I don't know if you can revert the behaviour but you are referring to  cinnamon-settings window there the Backgrounds window is empty.
On the other hand you can change the background via gnome-control-center but (sometimes) it also seems to affect the login screen.

---

### Post by stinkeye on 2013-06-27
Installing cinnamon from the Cinnamon stable ppa removes gnome-screensaver and installs cinnamon-screensaver.
Reinstalling gnome-screensaver will remove cinnamon-screensaver and some cinnamon functionality.
```
sudo apt-get install gnome-screensaver
```

Cinnamon from the Cinnamon stable ppa also installs nemo file manager which takes control of the desktop at startup.
(Affects the desktop right click menu)
Disable nemo from starting in the Ubuntu session.
```
gksudo gedit /etc/xdg/autostart/nemo-autostart.desktop
```
and change the line...
```
OnlyShowIn=GNOME;Unity;
```
to
```
OnlyShowIn=GNOME;
```
...and save.

---

### Post by LMDevlin on 2013-07-01
That seems to have done the trick, thank you very much.

---

### Post by berthold1 on 2014-02-16
I tried 
```
gksudo gedit /etc/xdg/autostart/nemo-autostart.desktop
```
[FONT=Ubuntu Mono][COLOR=#000000]and changed [/COLOR][/FONT]```
OnlyShowIn=GNOME;Unity;
``` [FONT=Ubuntu Mono][COLOR=#000000]to [/COLOR][/FONT]```
OnlyShowIn=GNOME
``` [FONT=Ubuntu Mono][COLOR=#000000]That worked once.
Then I changed [/COLOR][/FONT]```
Exec=nemo -n
```[FONT=Ubuntu Mono][COLOR=#000000]to [/COLOR][/FONT]```
Exec=nautilus -n
```[FONT=Ubuntu Mono][COLOR=#000000]
now it works every time.[/COLOR][/FONT]

---

