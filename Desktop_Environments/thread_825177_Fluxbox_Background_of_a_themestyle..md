---
title: "Fluxbox: Background of a theme/style."
date: 2008-06-10
forum: Desktop Environments
---

### Post by Uzi304 on 2008-06-10
After I install a new theme/style on Fluxbox, the background does not change. I cannot manually change the background either. Any help?

---

### Post by Nythain on 2008-06-10
fbsetbg /path/to/background/image.whatever work at all???

---

### Post by atomkarinca on 2008-06-10
There are two ways. As Nythain mentioned you can add that command to your ~/.fluxbox/startup like this:

```
fbsetbg /path/to/file/filename.extension &
```

or if you also use Gnome, you can change the wallpaper from gnome-appearance-properties and you can add it to startup:

```
gnome-settings-daemon &
```

Don't forget to add the ampersand (&) at the end.

---

### Post by HandyAndy on 2008-06-11
There are two ways to set the background in Fluxbox: globally and for a specific style. The global background will be used with any style that doesn't set its own background, but the style background will override the global background.

There are different ways of setting the global background, but the easiest I've found is to use **gsetroot**. It's in the repos and it's a little GUI frontend to **esetroot**, which you'll already have if you installed the latest Fluxbox from the repos.

To set a specific background for a specific style you need to edit the style's file in **~/.flubox/styles** using **background**. Using **background** is explained here:

[http://fluxbox-wiki.org/index.php/Background](http://fluxbox-wiki.org/index.php/Background)

As it says in the wiki, **background** has replaced **rootCommand**, but I've found that a lot of styles that specify their backgrounds still use **rootCommand**. Assuming you're using the current Fluxbox, you need to edit the style to use **background** to get it to work.

The wiki also covers alternative ways to set the global background, if you don't want to use **gsetroot**.

(Another thing I found when trying to get styles to work properly is that the specified fonts don't always work without some tinkering. This applies to a couple of the **artwiz** fonts, and may apply to others. For example, one style specified the **mints-strong** font, but it wasn't working. Everything looked ok because the name of the font's **.pcf** file was as it was specified in the style file - with the hyphen. But when I looked at its properties, the font's 'real' name is **mintsstrong**. I changed it to that in the style file and it worked.)

---

