---
title: "Making a shortcut to a wine app"
date: 2009-06-10
forum: General Help
---

### Post by Immortaly007 on 2009-06-10
Today I wanted to make a shortcut to a .exe file in my home folder. So i used "edit menu's", and in my menu (Wine - Programmes) I added a starter (an application, using as command line the address of my application).
But when I click on it nothing happens. I can however open the .exe by just double clicking on it in Nautilus.

---

### Post by robert shearer on 2009-06-10
Not sure I am with you on this one?

I usually do this Applications=>Wine=>Programs etc untill I have navigated to the program I want a shortcut to then right click and choose 'add this launcher to desktop" (or panel)

---

### Post by Entropy_Sam on 2009-06-10
> **robert shearer said:**
> Not sure I am with you on this one?
 
I usually do this Applications=>Wine=>Programs etc untill I have navigated to the program I want a shortcut to then right click and choose 'add this launcher to desktop" (or panel)
 
Normally this works fine, but if you're running a windows game/app which doesn't install a launcher on the Wine Menu, and/or relies on the app being run from a self-contained install directory, it won't work.
 
To put a Dwarf Fortress launcher on my desktop, for instance, I took a number of steps:
 
1. Right-Clicked a Wine app with a launcher installed on the "Start Menu" and chose "add this launcher to desktop"
 
2. Right-clicked that and took a look at the terminal command used to run a Wine App (if your app doesn't need to run from a self-contained directory, you'll just need to edit the launcher command for the app you're trying to run, and change the icon. If it doesn't work after trying that, keep reading)
 
3. Created a shell script in my Dwarf Fortress directory to (A) cd to the Dwarf Fortress Directory and then (B) run DF.exe (iirc the filename) using Wine.
 
4. Created a launcher on the Desktop to run the script.
 
5. I think the default launcher icon is ugly, so went and used GIMP to put together a "dwarf" icon using the "mining dwarf" logo on the Dwarf Fortress wiki.
 
If anyone wants to see my example shell script, let me know and I'll post it here when I get home later...
 
EDIT:
> **Immortaly007 said:**
> But when I click on it nothing happens.
Try running the launcher from the terminal and see what error message you get, if any.

---

### Post by Immortaly007 on 2009-06-10
Well I tried both. Using as a command line for the launcher:
/home/immortaly007/Games/Game/game.sh

and game.sh is containing the following:
```
#!/bin/sh
wine game.exe
```If i just run that script from nautilus it starts the game like it is supposed to.
But when I click on the launcher, the only thing it does is change my mouse into the "working" icon for a few moments (around 10 sec). And then the mouse returns to normal. Nothing happened...

Here is a screenshot showing you how it looks:
[http://dl.getdropbox.com/u/351481/Foto%C2%B4s/Ubuntu%20Screens/Launcher%20not%20working.png]("http://dl.getdropbox.com/u/351481/Foto%C2%B4s/Ubuntu%20Screens/Launcher%20not%20working.png")

btw If you're wondering why my CPU usage is so high, gnome do seems to have a problem and it is just indexing all the time using a lot of CPU and i am rescanning my media library using banshee. And the song i was listening is a coïncidence really xD

---

### Post by Entropy_Sam on 2009-06-10
What's the location of 'game.exe' in your filesytem?

Try editing your game.sh file so it looks like this:

```
#!/bin/sh
**cd /path/to/game/**
wine game.exe

```


That should point the executable in the direction of all the other files it needs to run properly (it's probably looking in the wrong place for them).

As a working example, here's my Dwarf Fortress shell script, which I run from a desktop launcher:
```
#!/bin/bash
cd /home/sam/.wine/dosdevices/c:/Games/DwarfFortress
wine "dwarfort.exe"
```

It won't run without the cd statement.

---

### Post by Immortaly007 on 2009-06-10
Thank you! That did the trick. 
game.sh was in the same directory as game.exe, so i thought that wasn't necessary. Thank you for your help!

---

### Post by Entropy_Sam on 2009-06-10
Glad it worked :-)
 
That put me in mind of a question I've been meaning to ask, actually...
 
New thread time!

---

