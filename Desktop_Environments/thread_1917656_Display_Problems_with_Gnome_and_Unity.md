---
title: "Display Problems with Gnome and Unity"
date: 2012-01-30
forum: Desktop Environments
---

### Post by kalebmcc on 2012-01-30
I'm using Gnome 3.2.1 and Unity 4.28.0 and since rebooting my workstation today have encountered some strange graphical anomalies. 

Menubars have grayed out text and a line through them. Icons in many applications including Software Center have small white squares in the middle. Switches have some kind of white distortion behind them. Gnome's application menu sometimes doesn't display icons when searching. Caption buttons such as close and minimize are sometimes distorted or invisible.

As well, Chrome's Gnome Compatibility extension breaks and the gnome-shell extensions site tells me every single extension on the site is incompatible.

I used [this guide]("http://www.techdrivein.com/2012/01/install-latest-gnome-shell-332-in.html") in an attempt to update Gnome, and that's when these problems began to appear. Is there a way to fix this, or rollback to a working version?

---

### Post by 2F4U on 2012-01-30
What graphics card do you have and what graphics driver are you using?

---

### Post by kalebmcc on 2012-01-30
> **2F4U said:**
> What graphics card do you have and what graphics driver are you using?

I have a Radeon HD 5450 and am using the VESA CEDAR driver. 

I tried to activate proprietary fglrx drivers moments ago and can no longer un-mirror my dual monitors after rebooting (required virtual size does not fit available size: requested=(2960, 1050), minimum=(320, 200), maximum=(1680, 1680)), so that's fun too.

EDIT: In case someone finds this thread in the future, the above problem was fixed by editing xorg.conf, as described in socken23's post [here]("http://ubuntuforums.org/showthread.php?t=1883119"), though be sure to adjust the numbers next to virtual to fit your requested resolution.

---

