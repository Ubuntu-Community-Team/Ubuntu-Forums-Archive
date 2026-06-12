---
title: "qt nethack problem"
date: 2009-11-01
forum: Gaming &amp; Leisure
---

### Post by Commisar Jimp on 2009-11-01
I've been trying to find a graphic version of nethack. X and QT look like the only ones in synaptic, but QT is giving me some problems. It seems like its in the wrong proportions, the information area (where hit points, stats ect. are) is squished and overlaps itself, and the actual game is stretched too tall.
It looks like a resolution problem, but nethack doesn't have any options to change anything graphics wise.
I know I could use X, but I prefer QT, does anyone know what I should do?

---

### Post by Lithium Rain on 2009-12-04
Go to QT options and change the font to small. Then go to width and set it much higher than 16. Change height also if need be.

---

### Post by HawkFest on 2010-12-02
> **Lithium Rain said:**
> Go to QT options and change the font to small. Then go to width and set it much higher than 16. Change height also if need be.
My settings are:[INDENT]Width = left as it was by default
Height = 25 (so that it's not distorted)
Fonts = medium
[/INDENT]**However there's a [COLOR=DarkRed]problem[/COLOR]:** these option settings are _not persistent_, I have to set them back every time I launch NetHack, which is quite tedious!... Is there a file I could manually modify once and for all?

---

### Post by Rustybolts on 2010-12-02
Thats why i stopped playing and started playing Stone Soup.
[http://www.playdeb.net/updates/Ubuntu/10.10/?category=dungeon](http://www.playdeb.net/updates/Ubuntu/10.10/?category=dungeon)

---

### Post by ShouriChatterjee on 2011-02-28
Here is how to fix your problems:
(1) Copy /etc/nethack/nethackrc.qt to your home dir as .nethackrc.qt
(2) Edit .nethackrc.qt:
QT_TILEWIDTH=15
QT_TILEHEIGHT=18
QT_FONTSIZE=s

This should make life easy.

---

