---
title: "Steel Storm Episode 1 shortcut"
date: 2011-08-10
forum: Gaming &amp; Leisure
---

### Post by Baloeb on 2011-08-10
I don't know if this is the right forum for this, but does anyone know how to create a desktop shortcut for the game?  I've tried and I always get an error unless I'm clicking on the actual game in the folder.

---

### Post by jerrrys on 2011-08-11
whatever your clicking on to start the game.  can you drag it to the panel?

---

### Post by Rustybolts on 2011-08-11
create a text document ending .sh
In it write 
cd (path to folder where the executable is)
(executable name)

save your document
right click on your document goto properties then permissions then tick the box allow executable file as program.
You can also change the icons image by right clicking on this file going into permissions and clicking on its image then simpley select a picture for your icon.
Shortcut created.

If you want a shortcut in your panel open a terminal
type sudo alacarte
then add new item in desired location, click command and type the terminal commands required to open this application

---

### Post by Baloeb on 2011-08-12
OK, I'm having a problem.  For some reason I can't get the game to run in a terminal.  I can go into the folder and click on the steelstorm icon, but if I go to the folder in terminal and type steelstorm nothing happens.  It says: steelstorm: command not found.  I've checked and the icon is marked to allow executing as a program.  So the script does not work either.  Any ideas?

---

### Post by thatguruguy on 2011-08-12
> **Baloeb said:**
> OK, I'm having a problem.  For some reason I can't get the game to run in a terminal.  I can go into the folder and click on the steelstorm icon, but if I go to the folder in terminal and type steelstorm nothing happens.  It says: steelstorm: command not found.  I've checked and the icon is marked to allow executing as a program.  So the script does not work either.  Any ideas?

When you're in the correct directory, type the following:

```
./steelstorm
```

---

### Post by Baloeb on 2011-08-12
Thanks!

---

