---
title: "How can I run a program (selected from menu) as root?"
date: 2008-03-21
forum: Desktop Environments
---

### Post by ubuntoexpert on 2008-03-21
I am normally NOT logged in (I use Ubuntu 6.something) as root.  If I want to run a command line program as root, I can use su or sudo.  But if I choose to run a program from the gnome menu, it seems to always run as the user I am logged in as.  My question:  How can I select a program to run from a menu and tell the computer that I want to run it as root?

---

### Post by Patb on 2008-03-21
Ubuntoexpert. You can run the program using gksu (preferable to sudo) from a terminal.  If you are not sure what the actual command for the menu item is, use Gnome Alacarte to find the properties of the launcher command.  Take care running any program as root of course :).  

Hope this helps. Cheers, Pat.

---

### Post by fela on 2008-03-22
you can use the menu editor (right click menu, edit menus) to find the menu item, rightclick>properties, then put a 'gksu' in front (without quotes) of the command in the menu item properties.

---

### Post by POW R TOC H on 2008-03-22
You can open the whole directory that contains apps in sudo. Use ```
sudo nautilus [DIRECTORY PATH]
```
Or you can just ```
sudo [APP NAME]
```
If the app is installed, most likely it's binary is in /bin folder. You can open /bin with sudo-ed nautilus (shown above). Then, whichever app you open from htat folder, will be ope in sudo mode...
Hope this helps...

---

### Post by Patb on 2008-03-24
> **POW R TOC H said:**
> ... Or you can just ```
sudo [APP NAME]
```

For graphical programs, it would seem preferable to use **[COLOR="Sienna"]gksu[/COLOR]** rather than **[COLOR="Sienna"]sudo[/COLOR]**.  See [this thread]("http://ubuntuforums.org/showthread.php?t=730277") and [this link]("http://www.psychocats.net/ubuntu/graphicalsudo").  

Also, if no command is given, gksu will display a gui window that allows you to type in a  command  to  be run. (From "man gksu").  So it would be simple to include the "gksu" command within your menu (even though that would not be my choice). 

Cheers, Pat.

---

