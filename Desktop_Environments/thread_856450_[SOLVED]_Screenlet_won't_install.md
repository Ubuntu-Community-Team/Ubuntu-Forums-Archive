---
title: "[SOLVED] Screenlet won't install?"
date: 2008-07-11
forum: Desktop Environments
---

### Post by VargasTheBlind on 2008-07-11
I downloaded a screenlet, and I tried installing it through the Screenlet Manager, but it said the archive didn't contain a screenlet (it contains 3 .svg files, I don't know if that's a screenlet or not), so then I copied first the extracted folder, and then the .svg files separately in the /home/<username>/.screenlets folder, but still no dice. Help? I'm running Hardy.

Thanks,
Vargas

---

### Post by sayakb on 2008-07-11
Those 3 svg files are just images. Where did you download it from? What screenlet is it?

---

### Post by VargasTheBlind on 2008-07-11
This one right here:

[http://www.gnome-look.org/content/show.php/Black+theme+for+notes+screenlet?content=83386](http://www.gnome-look.org/content/show.php/Black+theme+for+notes+screenlet?content=83386)

---

### Post by mgmiller on 2008-07-11
What you need to do is copy the extracted folder, named blacknote, to the the following folder: /usr/share/screenlets/Notes/themes

You will need sudo privilages to do this, so you can use:
```
gksu nautilus
```Be careful as you can now use the gui to totally frak your system.

Then, just run the screenlet as normal and set it's preferences to the blacknote theme.

---

### Post by VargasTheBlind on 2008-07-12
Thanks, that did it.

---

