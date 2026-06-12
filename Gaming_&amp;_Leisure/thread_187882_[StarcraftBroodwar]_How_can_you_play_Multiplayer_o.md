---
title: "[Starcraft/Broodwar] How can you play Multiplayer on same Network (no Net) ?"
date: 2006-06-03
forum: Gaming &amp; Leisure
---

### Post by patrick295767 on 2006-06-03
[Starcraft/Broodwar] How can you play Multiplayer on same Network (no Net) ?
  
1/I installed broodwar, and would like to play with other friend in multiplayer 
(all pc's with linux and with Broodwar installed and running)
 
The IPX is not working, and neither the null cable ...
 
I would like to make use of the linux network to play 

Is there a way ??
  
2/ Additionally, I would like to avoid pressing SHIFT key + 1 for instance 
to select my unit1 group
- Just 1 key would be better for me.
  
Should I have a QWERTY ? Is there a cedega config to change this ?
  
Greetz

---

### Post by CitizenKane on 2006-06-03
I haven't tried it but I am guessing if you choose UDP for network play that should work just fine.  It will appear as an option if you get the latest patches off of battle.net.  Also, I am pretty sure that there is no way to change key bindings in starcraft.  The game is just a bit too old ](*,) .

---

### Post by krang on 2006-07-20
Sorry for bringing this up again, but:

I just installed wine to have some fun with good old games like Q3 and starcraft and this stuff. The games themselves work really fine and there are no problems neither with grafics nor sound. But I cannot make or join network games in all games.

Seems like a problem with udp? Have i just missed the install of package for that stuff?

---

### Post by goobers on 2006-07-20
If by Q3 you mean Quake 3, there is a native linux version availiable, the best of which imo is here: [http://www.icculus.org/quake3/](http://www.icculus.org/quake3/)

Also, are you running through a router, or some kind of firewall?

---

### Post by patrick295767 on 2006-07-20
For the old version and my european keyboard, xmodmap is very useful :
the code
```
#!/bin/sh
xmodmap -e "keysym 1 = 1 ampersand"
xmodmap -e "keysym 2 = 2 eacute"
xmodmap -e "keysym 3 = 3 quotedbl"
xmodmap -e "keysym 4 = 4 apostrophe"
xmodmap -e "keysym 5 = 5 parenleft"
xmodmap -e "keysym 6 = 6 minus"
xmodmap -e "keysym 7 = 7 egrave"
xmodmap -e "keysym 7 = 7 underscore"
xmodmap -e "keysym 8 = 8 ccedilla"
xmodmap -e "keysym 9 = 9 agrave"
xmodmap -e "keysym 0 = 0 parenright"
xmodmap -e "keysym equal = period"

```

For UDP, dont know yet :-(
  
I can play via COM1  ==== cross ==== COM1    cable type.

---

