---
title: "help installing Compiz fusion...."
date: 2007-07-08
forum: Desktop Effects &amp; Customization
---

### Post by Mia_tech on 2007-07-08
ok my box sais, I got compz and beryl installed but how do you get started and how do you verify if you video card is compatible for this, I tried starting Desktop Effects and I got " Desktop Effects could not be enabled"
any help?

---

### Post by Mia_tech on 2007-07-08
ok my box sais, I got compiz and beryl installed but how do you get it started and how do you verify if your video card is compatible for this, I tried starting Desktop Effects and I got " Desktop Effects could not be enabled"
any help?

---

### Post by ajmorris on 2007-07-08
compiz-fusion is different to beryl.... to install compiz fusion, you must have the compiz-fusion-plugins-main and optionally compiz-fusion-plugins-extras installed. to install these on feisty, add these repositories to your /etc/apt/sources.list file :

deb [http://download.tuxfamily.org/osrdebian](http://download.tuxfamily.org/osrdebian) unstable compiz-fusion-git
deb-src [http://download.tuxfamily.org/osrdebian](http://download.tuxfamily.org/osrdebian) unstable compiz-fusion-git


also what graphics card do you have? and do you have direct rendering enabled? (glxinfo in a terminal and scroll to the top to look for something like this : direct rendering: Yes

and also install emerald and emerald-themes

---

### Post by Nekiruhs on 2007-07-08
> **ajmorris said:**
> compiz-fusion is different to beryl.... to install compiz fusion, you must have the compiz-fusion-plugins-main and optionally compiz-fusion-plugins-extras installed. to install these on feisty, add these repositories to your /etc/apt/sources.list file :

deb [http://download.tuxfamily.org/osrdebian](http://download.tuxfamily.org/osrdebian) unstable compiz-fusion-git
deb-src [http://download.tuxfamily.org/osrdebian](http://download.tuxfamily.org/osrdebian) unstable compiz-fusion-git


also what graphics card do you have? and do you have direct rendering enabled? (glxinfo in a terminal and scroll to the top to look for something like this : direct rendering: Yes

and also install emerald and emerald-themes
for the last part just type ```
glxinfo | grep "direct rendering"
``` and it'll tell you yes or no.

---

### Post by ajmorris on 2007-07-08
> **Nekiruhs said:**
> for the last part just type ```
glxinfo | grep "direct rendering"
``` and it'll tell you yes or no.

ah thanks Nekiruhs, i knew it was possible to show just the rendering, but couldnt remember the command :)

---

