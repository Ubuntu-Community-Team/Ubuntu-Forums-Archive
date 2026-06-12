---
title: "LXDE Appearance Customization"
date: 2010-10-24
forum: Desktop Environments
---

### Post by Stan_1936 on 2010-10-24
I have decided to give Lubuntu a try.

I have installed it and have 3 questions about customizing LXDE:

1. If you want to download a new icon set(Faenza), how do you install it?
2. If you want to download a new window-border set, how do you install it?
3. Is there a way to install Docky in Lubuntu?

---

### Post by PhilGil on 2010-10-24
> **Stan_1936 said:**
> I have decided to give Lubuntu a try.
1. If you want to download a new icon set(Faenza), how do you install it?
2. If you want to download a new window-border set, how do you install it?
3. Is there a way to install Docky in Lubuntu?

For #1 and 2, it's not much different than Gnome.

For #1, untar the icon set into */home/username/.icons* (create the folder if it doesn't already exist) or *usr/share/icons* (as root). The new icons will be available in Preferences-->Customize Look and Feel.

For #2, be aware that Lubuntu uses Openbox as a window manager, so you need to use Openbox window borders (although you can combine them with GTK2 themes). Untar into* /home/username/.themes* (create the folder if it doesn't already exist) or *usr/share/themes* (as root). They can be accessed through Preferences-->Openbox Configuration Manager.

I don't see why Docky wouldn't work, but it might bring in so many dependencies that it could compromise performance (especially if you need compositing and/or big chunks of Gnome).

I'm loving Lubuntu on my netbook, its remarkably peppy.

---

### Post by Stan_1936 on 2010-10-24
> **PhilGil said:**
> ...
For #2, be aware that Lubuntu uses Openbox as a window manager, so you need to use Openbox window borders (although you can combine them with GTK2 themes). ....

How? Is there a way to do this? Say I've got a GTK2 theme that I want to use and I haven't downloaded any window borders.

4. Do I **_need_** to download an openbox window border? Or would a GTK2 theme, by itself, work?

5. If the answer to 4. is yes, then (assuming that I've downloaded an openbox border) how would I go about combining the window borders with a GTK2 theme?

6. BTW, by openbox borders, I'm assuming you mean these:[http://box-look.org/index.php?xcontentmode=7402&PHPSESSID=256346df1b1b277c74ee97a1ded5101c](http://box-look.org/index.php?xcontentmode=7402&PHPSESSID=256346df1b1b277c74ee97a1ded5101c)
Correct?

---

### Post by PhilGil on 2010-10-24
> **Stan_1936 said:**
> How? Is there a way to do this? Say I've got a GTK2 theme that I want to use and I haven't downloaded any window borders.

4. Do I **_need_** to download an openbox window border? Or would a GTK2 theme, by itself, work?

5. If the answer to 4. is yes, then (assuming that I've downloaded an openbox border) how would I go about combining the window borders with a GTK2 theme?

6. BTW, by openbox borders, I'm assuming you mean these:[http://box-look.org/index.php?xcontentmode=7402&PHPSESSID=256346df1b1b277c74ee97a1ded5101c](http://box-look.org/index.php?xcontentmode=7402&PHPSESSID=256346df1b1b277c74ee97a1ded5101c)
Correct?

For the GTK2 themes, just untar into one of the two themes folders I mentioned in my previous post. You can then access them through the Look and Feel menu. The only potential issue is that you may have to install the appropriate GTK theme engine to get it to look right.

#4 You do not need to download additional window borders, there are a few different ones available by default. You can mix and match borders with GTK themes, just like in Gnome.

#5 Select the GTK theme you want from *Preferences-->Customize Look and Feel *and the border you want from *Preferences-->Openbox Configuration Manager*.

#6 Yes, correct. Some of those are complete themes that come with a GTK, some are window borders only.

---

