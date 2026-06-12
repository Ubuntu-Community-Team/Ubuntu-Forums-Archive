---
title: "Flux box help"
date: 2010-01-11
forum: Desktop Environments
---

### Post by t1nm@n on 2010-01-11
hello... i installed fluxbox from the package manager ..
now i want ti to look like the pic in the following link..pls tell me how

[http://navynos.linux.pl/files/navynos/screen1.jpg](http://navynos.linux.pl/files/navynos/screen1.jpg)

also guys ...the filemanger called tuxcommander rocks...giv it atry it is in the repositories

---

### Post by kerry_s on 2010-01-11
thats pretty standard, should be easy if your familiar enough with fuxbox.

first i'd look for the theme: [http://customize.org/fluxbox/themes](http://customize.org/fluxbox/themes)
the background might be a little harder, but i'm sure you'll find something.
there are lots of apps for the slit, i'd go with conky instead of that.

---

### Post by t1nm@n on 2010-01-11
thanx a lot....
but i'm a bit of a noob... so can u point out some links of how i can actually do that

---

### Post by kerry_s on 2010-01-11
have ya read the how to's ?
[http://fluxbox-wiki.org/index.php?title=Category:Howtos](http://fluxbox-wiki.org/index.php?title=Category:Howtos)

---

### Post by t1nm@n on 2010-01-11
yeah i've read it
for setting the background in the themes open theme file and got to the line rootcommand... but most of the theme files dont have that then also if i added that line nothing happens...this is one of the customizing problems i have

---

### Post by HandyAndy on 2010-01-12
Here's something I posted a while ago that you might find useful:

> There are two ways to set the background in Fluxbox: globally and for a specific style. The global background will be used with any style that doesn't set its own background, but the style background will override the global background.

There are different ways of setting the global background, but the easiest I've found is to use **gsetroot**. It's in the repos and it's a little GUI frontend to **esetroot**, which you'll already have if you installed the latest Fluxbox from the repos.

To set a specific background for a specific style you need to edit the style's file in **~/.flubox/styles** using **background**. Using **background** is explained here:

[http://fluxbox-wiki.org/index.php/Background](http://fluxbox-wiki.org/index.php/Background)

As it says in the wiki, **background** has replaced **rootCommand**, but I've found that a lot of styles that specify their backgrounds still use **rootCommand**. Assuming you're using the current Fluxbox, you need to edit the style to use **background** to get it to work.

The wiki also covers alternative ways to set the global background, if you don't want to use **gsetroot**.

(Another thing I found when trying to get styles to work properly is that the specified fonts don't always work without some tinkering. This applies to a couple of the artwiz fonts, and may apply to others. For example, one style specified the **mints-strong** font, but it wasn't working. Everything looked ok because the name of the font's **.pcf** file was as it was specified in the style file - with the hyphen. But when I looked at its properties, the font's 'real' name is **mintsstrong**. I changed it to that in the style file and it worked.)

I also use **gtk-chtheme** to preview and switch GTK+2x themes. **LXAppearance** does the same thing, plus it can preview/change the icon set too, although for some reason I've never been able to get it to do that properly for me. Both are in the repos.

---

### Post by t1nm@n on 2010-01-24
thats beatiful... thanx a bunch......

---

