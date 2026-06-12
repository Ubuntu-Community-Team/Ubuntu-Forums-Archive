---
title: "Which Config File Changes Desktop Icon Font Size in LXDE"
date: 2012-03-28
forum: Desktop Environments
---

### Post by ikodel on 2012-03-28
Hello all, I'm new here, but have some experience with *nix style OS.

I want to change the desktop icon font size.

**Please don't tell me how to do this using a GUI. I want to edit a config file.**

I've read many forum posts on the net on right clicking the desktop and choosing preferences...blah blah, but it's not so simple on my configuration, so...

If someone can direct me to the location of the config file that is responsible for **desktop icon font size and type** in Lubuntu using LXDE desktop, I would be very appreciative.

Thank you in advance.

---

### Post by ikodel on 2012-03-28
Ok so I solved this one myself.

The file is:

/home/user/.config/pcmanfm/LXDE/pcmanfm.conf

To change the desktop font to Droid Sans Fallback for example, replace the desktop_font entry with: 

**desktop_font=Droid Sans Fallback 8**

Changes will take place on next boot.

---

### Post by Rodney9 on 2012-03-28
For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

