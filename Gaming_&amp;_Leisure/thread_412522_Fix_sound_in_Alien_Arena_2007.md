---
title: "Fix sound in Alien Arena 2007"
date: 2007-04-18
forum: Gaming &amp; Leisure
---

### Post by RomeReactor on 2007-04-18
Hi. I don't know if someone else has already posted a solution to this issue, but here goes: This is just a repost of a comment I made on [this thread]("http://ubuntuforums.org/showthread.php?t=410914"), but I think some people might have less trouble finding this answer here.

If anyone is having trouble with the sound in Alien Arena 2007 (downloaded from one of the mirrors offered on [their site]("http://red.planetarena.org/")), the solution is to open the **AlienArena** file inside the **alienarena2007** folder

```
gedit /PATH/TO/alienarena2007/AlienArena
```

and changing this line

```
./crx.$acmd +set game arena $*
```

adding **sdl.** after **crx.**, so the file looks like this

```
#!/bin/sh
  
acmd=`uname -m`

./crx.**sdl.**$acmd +set game arena $*
exit $?
```

Don't overlook the periods. Granted the sound in the menu is crackly, but it sounds better during gameplay.

To run the game, open a terminal and change to the alienarena2007 directory; in my case it would be

```
cd /home/sho/.games/alienarena2007
```

and then

```
./AlienArena
```

To make a launcher in "Applications-->Games" right-click on the menu and select "Edit Menus"; add a new entry under "Games", enter **Alien Arena 2007** as the name (or whatever you like) and on the "Command" section, enter

```
sh -c "cd /PATH/TO/alienarena2007 && ./AlienArena"
```

To add the icon, press the icon button and navigate to the alienarena2007 folder and use the one that's there (alienarena.xpm). I hope this helps.

---

### Post by fakie_flip on 2007-05-17
muchas gracias. sound works now!

---

