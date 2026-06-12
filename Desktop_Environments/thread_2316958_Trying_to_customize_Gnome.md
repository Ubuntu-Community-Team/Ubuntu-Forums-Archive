---
title: "Trying to customize Gnome"
date: 2016-03-12
forum: Desktop Environments
---

### Post by Jakub_Brodzinski on 2016-03-12
Hello !
[COLOR=#111111][FONT=Ubuntu]I wanted to change something and I installed GNOME(via sudo apt-get install gnome). I started using GNOME Classic ,and I really like it, the only think I'd like to change is the colour of the bars at the bottom and the top. They're bright and I'd like to change it to the darker colour for example to the same colour that is in Ubuntu. Is there any way I can do it ? I found on the forums that combination of the keys Alt+RightMOuse or Alt+Super+RightMouse should give me some options but sadly It doesn't do anything .[/FONT][/COLOR]

---

### Post by buzzingrobot on 2016-03-12
Pretty sure the appearance of those panels is controlled by the theme in use. 

 Gnome uses Gnome Shell themes that apply to the panel, the Dash, etc., and GTK themes that apply to GTK apps. 

The dark Unity colors are in its default Ambiance theme.  Here's one reputable source of themes for Ubuntu. They have a number of PPA's, if you want to use them.  Notice the themes are categorized by release versions because themes are typically version-specific.  The links point to articles that contain instructions on how to install the themes.  [http://www.noobslab.com/p/themes-icons.html](http://www.noobslab.com/p/themes-icons.html)

Install "gnome-tweak-tool" so you can enable new themes once you've installed them

---

### Post by goofprog on 2016-03-12
Yes, there is a way.  I do not know how but there are GTK 2.0 themes for gnome classic and I had no idea how to put them into the desktop environment.  I just quit on that problem.

---

### Post by Frogs Hair on 2016-03-14
> **Jakub_Brodzinski said:**
> Hello !
[COLOR=#111111][FONT=Ubuntu]I wanted to change something and I installed GNOME(via sudo apt-get install gnome). I started using GNOME Classic ,and I really like it, the only think I'd like to change is the colour of the bars at the bottom and the top. They're bright and I'd like to change it to the darker colour for example to the same colour that is in Ubuntu. Is there any way I can do it ? I found on the forums that combination of the keys Alt+RightMOuse or Alt+Super+RightMouse should give me some options but sadly It doesn't do anything .[/FONT][/COLOR]

The instructions you found are for the the gnome-session -flashback or fallback depending on Ubuntu version. The Gnome Classic session uses Gnome Shell themes as buzzingrobot stated. Gnome 2 themes aren't applicable to either session.

---

### Post by Jakub_Brodzinski on 2016-03-14
> **buzzingrobot said:**
> Pretty sure the appearance of those panels is controlled by the theme in use. 

Gnome uses Gnome Shell themes that apply to the panel, the Dash, etc., and GTK themes that apply to GTK apps. 

The dark Unity colors are in its default Ambiance theme. Here's one reputable source of themes for Ubuntu. They have a number of PPA's, if you want to use them. Notice the themes are categorized by release versions because themes are typically version-specific. The links point to articles that contain instructions on how to install the themes. [http://www.noobslab.com/p/themes-icons.html](http://www.noobslab.com/p/themes-icons.html)

Install "gnome-tweak-tool" so you can enable new themes once you've installed them

Using gnome tweak tool changes colour of everything but bars at the top and bottom :(.

---

### Post by kurt18947 on 2016-03-14
There are a couple gnome shell extensions to change the color and brightness of the panel(s). I don't know that they'd work in other than gnome shell though.

---

### Post by Jakub_Brodzinski on 2016-03-14
I found some tips/themes ([http://itsfoss.com/install-switch-themes-gnome-shell/](http://itsfoss.com/install-switch-themes-gnome-shell/)). Sadly it works only in "normal" GNOME ,not GNOME CLASSIC ...

So there is a way to make your own bar at the botton in 'GNOME' (not classic) with GNOME extensions,after that u can easly customize it add/remove things.This thread can be closed .

---

### Post by buzzingrobot on 2016-03-15
> **Jakub_Brodzinski said:**
> Using gnome tweak tool changes colour of everything but bars at the top and bottom :(.

Believe you need a Gnome Shell theme for that, which is distinct from a GTK theme. Thetrick is finding two that match.

You will also need the User Themes extension installed to change Shell themes.

---

### Post by kurt18947 on 2016-03-24
> **buzzingrobot said:**
> Believe you need a Gnome Shell theme for that, which is distinct from a GTK theme. Thetrick is finding two that match.

You will also need the User Themes extension installed to change Shell themes.

The gnome shell extension "taskbar" will change the background color of both top & bottom panel ('bar'). That extension didn't work well for me in its earlier iterations but the current version in 16.04 seems pretty good.

---

