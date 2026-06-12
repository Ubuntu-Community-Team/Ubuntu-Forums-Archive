---
title: "Unity Background Colour Forced to be Black"
date: 2013-05-09
forum: Desktop Environments
---

### Post by tbrminsanity on 2013-05-09
Good day,

I'm running Ubuntu 13.04 and I've noticed something that is very annoying in the Appearance settings.  If I select Colours & Gradients, or if I choose a background colour for a wallpaper, it doesn't matter what colour I choose.  It always uses the colour black.  Does anyone know what is the issue and how I can fix it?  In an ideal world I would be able to use a combination of a Gradient and a Wallpaper (like I used in Gnome under 9.10) but I will settle with being able to select a background colour.
Besides this one annoyance, I really like Unity and I prefer it to Gnome.  It would be nice if there were more themes available (maybe if Canonical would create a themes.ubuntu.com site or something like that), but again I'm happy with what I have right now.

---

### Post by mc4man on 2013-05-10
solid colors is broken other than the 3 default supplied choices (blue with 2 gradient choices.
Once you try other colors & or gradients then you'll also likely lose those orig. 3 or some of.

The issue is that from the Appearances panel when you choose a custom solid color or gradient it writes to dconf as rgb(XXX,,XXX,X) which only produces black.
To fix - 
open dconf-editor > org.gnome.desktop.background
Reset the Primary & Secondary colors back to defaults (highlight key, click on set to default button

To use a custom solid color & or gradient
You must enter the color directly in dconf-editor, (in above schema/keys), use chosen color(s) as #XXXXXX

edit:
Set as either solid or with a gradient in the top key (color-shading-type

---

### Post by Frogs Hair on 2013-05-10
This is a bug , see post # 6. [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1138251](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1138251)

---

### Post by tbrminsanity on 2013-05-11
Thank you that worked.  I'm going to look into creating a patch for this if possible.

---

### Post by grahammechanical on 2013-05-11
As for themes you can search here for GTK3 themes and get some results.

[http://www.webupd8.org/](http://www.webupd8.org/)

You will need GTK 3 themes not GTK 2 themes. I have not tried any of these and I do not know how to install them. The 13.04 Software Centre has Unity Tweak Tool. It may be useful for installing a theme. I would not know. Also 

[https://launchpad.net/~upubuntu-com/+archive/gtk3](https://launchpad.net/~upubuntu-com/+archive/gtk3)

[http://www.upubuntu.com/search/label/Themes](http://www.upubuntu.com/search/label/Themes)

[http://gnome-look.org/index.php?xcontentmode=167](http://gnome-look.org/index.php?xcontentmode=167)

Regards.

---

