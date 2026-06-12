---
title: "gnome desktop mixed up"
date: 2007-11-30
forum: Desktop Environments
---

### Post by AlmaTlust on 2007-11-30
Hi,
I normally use KDE with integrating the few Gnome programs via the QT style. Recently I installed ubuntu-desktop to give it a try. But it is mixed up. When using the Baghira theme for KDE, all the menues appear black. After switching to another theme (plastik), all Gnome windows appear empty - no icons, nothing to click on, text is invisible and so on.
How can I solve this?

---

### Post by AlmaTlust on 2007-11-30
I forgot to say - I use Gutsy, and the problem is worse when I fire up Gnome than when I use Gnome programs from within KDE

---

### Post by TeaSwigger on 2007-12-01
Unfortunately that's going to happen, as ubuntu and kubuntu still haven't implimented a completely independant theme management. There are a number of factors involved, and I haven't sorted them all.

1) ubuntu / gnome.

2) GTK 2x

3) GTK 1x

4) kubuntu / KDE

5) Qt 3x

6) Qt 4x

7) ubuntu controls of GTK 2x.

8 ) kubuntu controls of GTK 2x.

etc.

gnome-settings-daemon takes control of GTK 2x and partially 1x when Gnome is used; I  don't know KDE's equiv, but in KDE you set the Qt theme, and KDE tries to control GTK 2 to resemble the Qt theme selected and to get GTK 2x and 1x to use the KDE selected colors. Note the hidden files in your user home folder: there are gtkrc config files gnome and kde use. You can further complicate this by using gtk-theme-switch (in the repositories), which creates "proper" gtkrc config files that over ride the gnome & kde ones sometimes sort of.

In short it's a mess. With persistence maybe you can work out methods to create a few consistent themes. Hope this helps somehow.

---

### Post by AlmaTlust on 2007-12-03
Well, somehow it kind of fixed itself without me understanding how... At the moment both KDE and Gnome programs look fine in both environments, and I will be VERY careful not to touch anything! ;-)

---

