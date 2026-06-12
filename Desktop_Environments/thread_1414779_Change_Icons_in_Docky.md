---
title: "Change Icons in Docky?"
date: 2010-02-24
forum: Desktop Environments
---

### Post by javyn999 on 2010-02-24
Hey all.  Is there a way to change the icon images for my applications in Docky?

---

### Post by sensory on 2010-03-04
If you go to usr/share/applications (gksu nautilus usr/share/applications) and change the application's icon there, then drag it from that folder to your Docky bar, it should display your custom icon.

Hopefully. :)

---

### Post by kendoori on 2010-03-12
this works reliably in Gnome-Do's version of Docky, but no in the standalone version (Docky 2). In many cases Docky 2 sort of his its own mind about what icons it uses. In fact, it's kind of unusable to me until they make it so that you can 100% control this. I've reverted to Gnome-Do Docky until they sort this out.

---

### Post by narutouzamaki on 2010-07-24
if you want to change the icon all you have to do is remove the original icon from docky and then for instance if you wanted to change mozillas icon then go into applications and drag mozilla onto your desktop once its there right click on the shortcut and go to properties and click on the icon and you can change it!

---

### Post by jeddycakes on 2010-08-02
I found a sort of fix for this.

Open up your desired icon in gimp and resave as .png to your desktop. There probably is a max size, but I used a scalable icon (for example, I was changing CoverGloobus) and it worked fine.

Then I opened up usr/share/CoverGloobus (or any path you require) and simply dropped and swapped the icons.

I appreciate that paths to programs differ throughout the system, you just have to adapt and overcome :) usually usr/share/applications is a good bet, but be careful again with icon sizes as too big icons crash docky. Unpleasantly.

Have fun, hope this helps!

---

### Post by Ginsu543 on 2010-08-04
I've been able to use custom icons for all the launchers on Docky (standalone, not Gnome-Do) by figuring out where the original icons are located and copying the custom icon there (well, I first rename the old icon *.png.old, copy the custom icon to the directory, and rename it the same as the original icon). As for where many of the icons are located, check out:

1) /usr/share/pixmaps
2) /usr/share/icons
3) /usr/share/icons/hicolor/scalable/apps

---

