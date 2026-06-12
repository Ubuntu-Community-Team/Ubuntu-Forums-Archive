---
title: "transparent panels in gnome-flashback-metacity on Ubuntu 17.04"
date: 2017-05-25
forum: Desktop Environments
---

### Post by koldrakan on 2017-05-25
I have recently installed the gnome-flashback package in my fresh Ubuntu 17.04, and I want to make the panels transparent like I always do. But apparently that's not an option anymore. 
Is there any way to do it? Alt+rightclicking on the panel gives me a small menu, but no transparency options. I have also looked for the config file but I can't seem to find it. 
I'd like to keep using metacity to conserve resources, if possible.

---

### Post by muktupavels on 2017-05-25
Use background color option under Theme tab. Color picker allows to change opacity...

---

### Post by koldrakan on 2017-05-25
Yes, there is an opacity bar there, but it doesn't seem to do anything. You can add a background, but changing the opacity of the background colour does nothing

---

### Post by muktupavels on 2017-05-25
Yes, I noticed that it does not work with Ambiance...

You can edit ~/.config/gtk-3.0/gtk.css or create if it does not exist. You can add `panel-toplevel { background-image: none; }` to unset background image from Ambiance theme. Then background color setting should work. Or you can add `panel-toplevel { background: transparent; }` and not use gnome-panel theme settings.

---

