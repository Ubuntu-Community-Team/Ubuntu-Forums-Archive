---
title: "Wallpaper system wide in /usr/share/wallpapers?"
date: 2007-04-25
forum: Desktop Environments
---

### Post by snowstorm on 2007-04-25
I was wondering whether somebody could help me with a simple question. I would like to make a wallpaper available system wide. How can I do it?

I've seen the default wallpapers in /usr/share/wallpapers, but they also contain .desktop files, which seems to suggest that something more has to be done than just copying a jpg to that folder...

---

### Post by YourSurrogateGod on 2007-04-25
Right click on Desktop and select Change Desktop Background?

What do you mean exactly? You want the same wallpaper displayed on all desktops that are on your system?

---

### Post by snowstorm on 2007-04-26
I figured out what the problem was. I copied some jpg's to /usr/share/wallpapers, but I didn't see them listed in the system settings where I choose the background. The reason turned out to be that those files had some metainfo inside the jpg, which is then displayed rather than the filename. Deleting the metainfo was all I had to do for the filename to show up as expected.

---

### Post by mmerlone on 2008-05-26
> **snowstorm said:**
> Deleting the metainfo was all I had to do for the filename to show up as expected.

And how exactly you did that?

---

