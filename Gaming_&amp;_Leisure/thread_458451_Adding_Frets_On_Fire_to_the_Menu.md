---
title: "Adding Frets On Fire to the Menu"
date: 2007-05-29
forum: Gaming &amp; Leisure
---

### Post by ep2011 on 2007-05-29
First of all, I want to say I've been trying to see why this isn't working for awhile, i've been trying and it hasn't been working. 

I downloaded Frets on Fire and put it in my home folder as ./FretsOnFIre

Now, when I make the file /usr/share/applications/Frets-on-fire.desktop I put the following in it

> [Desktop Entry]
Encoding=UTF-8
Name=Frets On Fire
Comment=A Game similar to Guitar Hero
Exec=/home/eric/.FretsOnFire/FretsOnFire
Icon=/home/eric/.FretsOnFire/data/icon.png
Terminal=false
Type=Application
Categories=Application;Game;

The Icon shows up okay, but when I click on it, nothing happens.

When I type cd /home/eric/.FretsOnFire/ && ./FretsOnFire it works perfectly... I think I know what it is, I think the command Exec=/home/eric/.FretsOnFire/FretsOnFire wants to go to FretsOnFire.bin, but I need it to just go to FretsOnFire... Any ideas on this?

Edit: it isnt that ^^. I just made copied the file as FoF and changed it to Exec=/home/eric/.FretsOnFire/FoF and it still doesnt work.

---

### Post by DoktorSeven on 2007-05-29
Probably needs to be inside the directory when you execute the program.  Make a launcher somewhere with the following:

```

#!/bin/bash

cd /home/eric/.FretsOnFire
./FretsOnFire

```

Make it executable (either by its properties in the file browser or **chmod 755 *nameoflauncher*** from the Terminal).

Then have the desktop entry point to the launcher (the Exec= line).

---

### Post by RomeReactor on 2007-05-29
Hi. You can also change **Exec=/home/eric/.FretsOnFire/FretsOnFire** to **Exec=sh -c "cd /home/eric/.FretsOnFire && ./FretsOnFire"**.

---

### Post by ep2011 on 2007-05-30
Worked perfectly, thanks. It also worked for Stepmania (With a little tweaking as well).

---

### Post by douradinhos on 2007-07-11
tks, works great for me too:KS

---

