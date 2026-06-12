---
title: "Getting GTK apps to use GTK-QT in root"
date: 2006-01-06
forum: General Help
---

### Post by NeoChaosX on 2006-01-06
Okay, I'm having trouble getting GTK apps running in root mode to use the GTK-QT engine. I've tried doing **kdesu kcontrol** and adjusting the GTK settings from there, but when I run Synaptic, the program still usues the ugly default GTK theme when running. I do't know what I'm doing wrong, or what I should do, since appearntly all other threads on this forum tell me to do it though kcontrol as root. So can anyone help me out with this?

---

### Post by GeneralZod on 2006-01-06
Same here.  I'd love to hear a definitive, 100% working solution to this one! :)

---

### Post by louis_nichols on 2006-01-06
I kinda have the same problem

it's pretty weird, though. here's what I noticed: the gtk-qt library works in general, although sometimes you need to disable and re-enable the theme in system settings. this solved the problem for firefox and gaim, for example. but, synaptics looks even uglyer after that. it's like just a X window thing. But... that's only if I try to run it from the menu, or using kdesu (I think apps in the kmenu use that by default, because there the entry is simply synaptic, but if I try to run synaptic from the command line, it says I need to be root). If I use sudo synaptic in bash, it looks perfect. But.... being kinda of newb, I don't know what this means and how it helps.

Anyway, firefox acts weird after the gtk-qt thing. If I move the mouse cursor over some widgets or text in pages, they flicker. Kinda sucks. I just installed kubuntu today, after a month of ubuntu because I am a big fan of KDE, which I used for a year with Fedora. But I have to say, kubuntu doesn't seem to rise to the qualitt of either ubuntu or KDE.

---

### Post by NeoChaosX on 2006-01-08
I fixed it. A little searching helped me find this solution. Do these two commands:

```
sudo ln -s ~/.qt/qt_plugins_3.3rc /root/.qt/qt_plugins_3.3rc
sudo ln -s ~/.qt/qtrc /root/.qt/qtrc
```
Boom, you have Synaptic using QT widgets when running it from the menu now.

---

### Post by mayo on 2006-01-09
[QUOTE=NeoChaosX]I fixed it. A little searching helped me find this solution. Do these two commands:

```
sudo ln -s ~/.qt/qt_plugins_3.3rc /root/.qt/qt_plugins_3.3rc
sudo ln -a ~/.qt/qtrc /root/.qt/qtrc
```
Boom, you have Synaptic using QT widgets when running it from the menu now.[/QUOTE]

Guess that second command should be
```
sudo ln -s ~/.qt/qtrc /root/.qt/qtrc
```

But in any case, this didn't fix the problem for me.
I'm currently trying to get Firefox 1.5 to use QT, but no chance.
The FFox 1.07 that came with Kubuntu also didn't use the QT widgets at first, but reapplying the GTK theme in the System-Settings did the trick. But no luck now with 1.5

---

### Post by NeoChaosX on 2006-01-09
> **mayo]Guess that second command should be
```
sudo ln -s ~/.qt/qtrc /root/.qt/qtrc
```[/quote]

Oh crud. Corrected.  said:**
> But in any case, this didn't fix the problem for me.
I'm currently trying to get Firefox 1.5 to use QT, but no chance.
The FFox 1.07 that came with Kubuntu also didn't use the QT widgets at first, but reapplying the GTK theme in the System-Settings did the trick. But no luck now with 1.5
That's funny. Are starting Firefox as root, or just as a normal user. As a normal user, I'm getting Firefox to use GTK-QT just fine. What's your GTK style set to in  the KDE panel?

---

### Post by GeneralZod on 2006-01-09
Made a difference here; thanks a lot! :D

I don't have a before shot, though:

[http://etotheipiplusone.com/synaptic-gtk-qt.png](http://etotheipiplusone.com/synaptic-gtk-qt.png)

---

### Post by NeoChaosX on 2006-01-09
Okay, found another way around this without doing symlinks: Make sure root's KDE theme and font settings match your settings for KDE. So if you're using say, Plastik with size 9 Sans font, make sure the root user is also using Plastik and size 9 Sans (Color and window decorations, on the other hand, CAN be different form yours - I use a different color scheme to tell me I'm using a program as root).

---

### Post by Cyrus XIII on 2007-10-21
Thanks a lot! :)

---

