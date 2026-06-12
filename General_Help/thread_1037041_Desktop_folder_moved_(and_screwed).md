---
title: "Desktop folder moved (and screwed)"
date: 2009-01-11
forum: General Help
---

### Post by euclidsbrother on 2009-01-11
Hey guys..  I moved my Desktop folder from my home into a sub directory.. stupid move..   Next time i rebooted, my destop shows everything in my Home dir since the Desktop folder didn't exist.  I moved the Desktop folder back to my Home dir, but the desktop is not using it... it's still using the home dir.  (/home/EucdlisBrother).

Is there a config file somewhere that says what folder is used for the Desktop? Anyone know how I can undo this mess up?  I did try searching, but couldn't find anything relevent to this..

Thanks,
-EB

---

### Post by euclidsbrother on 2009-01-11
i guess if nothing else, i can create a new user, move my files over, delete the old user, then rename the new user to the old one..

---

### Post by Woody1987 on 2009-01-11
im not entirely sure how to fix it, but there is probably a way to solve it in the gnome configuration, open a terminal and type gconf-editor. This is kind of like a windows registry but for gnome. The setting your looking for should be in there.

---

### Post by stanz on 2009-01-11
Your 2nd post sounds easiest.
There is a configuration editor - gconf, or something...you can add it to your app menu.
Maybe someone will pass thru with directions...
Have fun!

---

### Post by linfidel on 2009-01-11
> **euclidsbrother said:**
> i guess if nothing else, i can create a new user, move my files over, delete the old user, then rename the new user to the old one..
There is a setting in the "Configuration Editor", which is in System Tools menu for me - but it seems like I had to enable it in the menu editor (**gconf-editor** from the command line).

Then drill down into /apps, nautilus, preferences, and look for the option "desktop_is_home_folder", and uncheck it.

---

### Post by euclidsbrother on 2009-01-11
Thanks guys.. That option was already unchecked..  Whatever special attribute that Desktop folder has, it lost it when it was moved.. and it just wouldn't use it anymore..  I ended up just creating a new user, deleting the first user and recrating it and restoring my custom files..

---

