---
title: "Transparent topbar"
date: 2008-03-22
forum: Desktop Effects &amp; Customization
---

### Post by wonko69 on 2008-03-22
Does anyone know how to set any theme up to look like this:
[http://www.linux.com/var/uploads/Image/articles/129757-1.png](http://www.linux.com/var/uploads/Image/articles/129757-1.png)

Thanks

---

### Post by MONODA on 2008-03-22
rightclick the top panel click properties. click the background tab, select solid color and make it transparent.

---

### Post by wonko69 on 2008-03-22
> **MONODA said:**
> rightclick the top panel click properties. click the background tab, select solid color and make it transparent.

When i try that with the theme I am currently running, Neon with a Pixmap engine, only the center part of the panel is transparent. 
So does this mean I have to edit the emereld theme or the metacity theme to allow the rest of the panel to be transparent?

Thanks

---

### Post by Lord Illidan on 2008-03-22
The metacity theme is probably setting a panel image. You have to go inside the theme folder, find that image and delete/rename it.

---

### Post by MONODA on 2008-03-22
yes you probably will have to.

---

### Post by wonko69 on 2008-03-22
> **Lord Illidan said:**
> The metacity theme is probably setting a panel image. You have to go inside the theme folder, find that image and delete/rename it.

Thanks for the help. I will start digging.

---

### Post by wonko69 on 2008-03-22
> **wonko69 said:**
> Thanks for the help. I will start digging.

Could'nt get it working the way I wanted. So I am going to go another route and create a theme from scratch my self. Thanks for the help and quick responce.

---

### Post by fela on 2008-03-22
two common places for themes are ~/.themes and /usr/share/themes just in case you don't know (start 'digging') :lolflag:

---

### Post by fela on 2008-03-22
> **wonko69 said:**
> Could'nt get it working the way I wanted. So I am going to go another route and create a theme from scratch my self. Thanks for the help and quick responce.

are you sure you want to make your own theme from scratch? it's very tedious.

the panel background image in your existing theme is probably in <themedirectory>/gtk-2.0/Panel/panel-bg.png, ('Panel' might be something else with 'Panel' inside its name) :)

---

### Post by wonko69 on 2008-03-22
> **fela said:**
> are you sure you want to make your own theme from scratch? it's very tedious.

the panel background image in your existing theme is probably in <themedirectory>/gtk-2.0/Panel/panel-bg.png, ('Panel' might be something else with 'Panel' inside its name) :)

I found the images but swapping them for some that were transparent didnt work. So I thought the best way was to find a new theme that had kinda the look I wanted and the customize that to my liking. So kinda from scratch :)

---

### Post by fela on 2008-03-23
do you have macmenu gtk hack installed by any chance?

---

### Post by wonko69 on 2008-03-24
> **fela said:**
> do you have macmenu gtk hack installed by any chance?

No I dont. What does that do?

---

