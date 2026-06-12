---
title: "icons won't change in xfce"
date: 2008-05-11
forum: Desktop Environments
---

### Post by rolypolycat on 2008-05-11
Hello!

I added some new icons into my .icon folder- a group of them under one folder called Favorite. I also added this same folder under ?usr/share/icons. When I got to Settings/User Interface, Icontheme, all I see are the default sets that came with Hardy Xubuntu, plus a few I downloaded from the repositories. How do I get the settings Manager to find the icon folder I want to use? Do icons have to be all one set of themes, so to speak; you can't simply collect a groupd of good, but separate ones, place them in a folder, and use that? And if you can, how do I go about this? I really like the bunch I've collected over the last 2 years, (especially the Firefox icon with the fox chewing on the Internet Explorer sysmbol!)
Any help is greatly appreciated!
Thanks!:confused:

---

### Post by denham2010 on 2008-05-11
Hi RolyPolyCat,

You are on the right track, but it's a little more involved than placing a folder of icons in /usr/share/icons.

The easiest way to see what you need to do is by opening /usr/share/icons and basically following the pattern inside.

Each icon theme is in a folder of that theme's name, as an example, open the folder rodent. This being the XFCE default.

Inside that folder, you will find more folders, based on the icon size, and within them, categories of icons for different purposes, ie devices, applications, mime types etc.

Also, in the rodent folder, you will see some other files; namely iconrc, iconrc-png and index.theme

These are the files that tell XFCE, Gnome or KDE that this is a theme of icons, and to display it for selection in the icon theme tab of the user interface selection tool, along with how each icon should be applied and used in the system.

So basically, you will need to structure your icons in a similar way as the other themes in /usr/share/icons and create a version of iconrc, icon-png and index.theme to match your theme (you can view these files in mousepad, gedit, kate to see how to construct your own).

It is not necessary to place your theme in /usr/share/icons, and being a system folder with only root permissions, I would not recommend it either.

You only need to place your completed theme in ~/.icons for it to be available to your system.

I hope this helps you on your way to creating your own icon themes!

---

### Post by Joe Kuan on 2009-05-21
You need to create iconrc file and update the theme/gtk2.0/gtkrc to point to your icon theme directory/iconrc.

I created a blog with some instructions and I hope this helps.

[http://joekuan.wordpress.com/2009/05/21/how-to-change-xfce4-themes-to-use-gnome-icons/]("http://joekuan.wordpress.com/2009/05/21/how-to-change-xfce4-themes-to-use-gnome-icons/")

---

### Post by Brandon Williams on 2009-05-21
Are these all alternate icons for applications? Or is it an icon theme? If it's an icon theme, then the previous discussions are what you want. If it's alternate icons for applications, then all you need to do is give the icon the correct name and put it in .icons. For example, I have an alternate application icon for seamonkey, ~/.icons/seamonkey.png. Look in /usr/share/pixmaps/ to see filenames and image types for existing applications, and look in /usr/share/applications/<appname>.desktop to figure out what the base icon name should be.

---

### Post by rolypolycat on 2009-06-16
Thanks everyone for your help! I haven't been here in a while, but I tried all the suggestions today, and I now have the Xquisite icon set and LightBlueShinyCursors in my Xubuntu. Looks really good! Thanks again!:D

---

