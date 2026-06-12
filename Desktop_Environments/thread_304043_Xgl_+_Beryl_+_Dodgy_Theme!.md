---
title: "Xgl + Beryl + Dodgy Theme!"
date: 2006-11-21
forum: Desktop Environments
---

### Post by mwob on 2006-11-21
Howdee,

I installed XGL and Beryl as per RacerII's guide over on the beryl forums, and all works well....except that for some reason the non beryl-controlled parts of the desktop look crap. The font is tiny, its dark grey, and all the icons on the taskbar are old-fashioned crappy ones... I can change the theme using emerald theme manager, but it doesn't make a difference to these bits...

Anyone else seen this? Its a shame because the "beryl" side of things worrks great!

Matt.

---

### Post by PhrankDaChickenGeek on 2006-11-21
You can change that part of the theme under "System -> Prefs -> Theme"

Download more themes (GTK 2.x, icon sets) at [http://www.gnome-look.org](http://www.gnome-look.org)

---

### Post by mwob on 2006-11-21
Sorry, I wasn't being specific enough..

When I don't choose XGL/Beryl as my desktop, I get the nice standard Ubuntu (Human) theme. When I choose the XGL desktop, its pretty nasty looking. If I change the theme as you suggested it makes no difference, so even though "Human" is my selected theme, it aint "human" that its using!

Matt.

---

### Post by yatt on 2006-11-21
> **mwob said:**
> Howdee,

I installed XGL and Beryl as per RacerII's guide over on the beryl forums, and all works well....except that for some reason the non beryl-controlled parts of the desktop look crap. The font is tiny, its dark grey, and all the icons on the taskbar are old-fashioned crappy ones... I can change the theme using emerald theme manager, but it doesn't make a difference to these bits...

Anyone else seen this? Its a shame because the "beryl" side of things worrks great!

Matt.
They changed how beryl loads, and RacerII hasn't updated his guide or a while.

You have to add gnome-settings-daemon IIRC (if that is not it, open a terminal and type gnome-set then press tab until it lists the correct name[I'm at school now and can't check]). This is the quick fix, and it is messy.


Alternatively, you could the beryl-project wiki, and look at the the ubuntu instructions. That Howto is the most up to date, and sne of your scripts will be different, rosm that howto (instead of exec gnome, it will be exec /usr/bin/xsession or something like that.

---

### Post by redDEADresolve on 2006-11-23
Yeah the default theme font sucks. I made one that look very much like the old default theme.

I had to zip it so the forums would allow me to upload it. Cheek out the screenshot, if you like it share it. That purple theme is super sissy.

---

