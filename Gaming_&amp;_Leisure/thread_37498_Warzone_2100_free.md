---
title: "Warzone 2100 free"
date: 2005-05-27
forum: Gaming &amp; Leisure
---

### Post by dolny on 2005-05-27
[http://www.strategyplanet.com/warzone2100/screens/](http://www.strategyplanet.com/warzone2100/screens/) - screenshots
[http://www.liflg.org/?catid=6&gameid=63](http://www.liflg.org/?catid=6&gameid=63) - loki installer (download the game for free)


WARZONE 2100 is a real time action and strategy game set on Earth in the 21st Century. Upon entering the post-nuclear world of Warzone 2100 you land from your transport and establish your base. Here you conduct research, design and manufacture vehicles, build new structures and prepare your plans of global conquest.

PS. I couldn't get the multiplayer mode to work :( :( :( I just see a blank screen with a background after clicking 'multiplayer'

---

### Post by bored2k on 2005-05-27
[QUOTE=dolny][http://www.strategyplanet.com/warzone2100/screens/](http://www.strategyplanet.com/warzone2100/screens/) - screenshots
[http://www.liflg.org/?catid=6&gameid=63](http://www.liflg.org/?catid=6&gameid=63) - loki installer (download the game for free)

WARZONE 2100 is a real time action and strategy game set on Earth in the 21st Century. Upon entering the post-nuclear world of Warzone 2100 you land from your transport and establish your base. Here you conduct research, design and manufacture vehicles, build new structures and prepare your plans of global conquest.

PS. I couldn't get the multiplayer mode to work :( :( :( I just see a blank screen with a background after clicking 'multiplayer'[/QUOTE]
 Is this legal ? I don't see any FREE banners on the main site .

edit - I will remove the download link until proven that this is legal .
edit 2 - Nevermind.

---

### Post by apollyonis on 2005-05-27
In the readme it says under "ToDo" Network stuff so I'm presuming that Loki never got networking, hence multiplayer, to work. Sorry. I'd like to play this on multiplayer too.  :neutral:

---

### Post by dolny on 2005-05-27
Yeah I've read that soon after I posted the thread but I couldn't reply (under Firefox it keeps telling me that I must specify a subject - even though I specified it) - I'm writing from Konqueror. I checked tutorial and first mission - seems kewl. Run it with -1024x768 argument - higher res.

---

### Post by bored2k on 2005-05-27
[QUOTE=dolny]Yeah I've read that soon after I posted the thread but I couldn't reply (under Firefox it keeps telling me that I must specify a subject - even though I specified it) - I'm writing from Konqueror. I checked tutorial and first mission - seems kewl. Run it with -1024x768 argument - higher res.[/QUOTE]
 So is it good ? I know its just 30MB but I dont like to waste time..

---

### Post by dolny on 2005-05-27
It will be great when they'll add the multiplayer option. I can't say that it's great after  a tutorial and one mission, but seems very cool at the moment - you can choose parts and build vehicles from them. The terrain is 3d, definately worth those 30megs in my humble opinion. Express your opinion after you check it.

Most sites I visited said that this is one of the greatest RTS' out there. Worth downloading.

> Status
Current tasks
We're currently rewriting the network code on top of SDL_Net. We might need testers soon so don't hesitate to contact me.
Woohoo!

PS. I like your playlist ;) Good bands.

---

### Post by apollyonis on 2005-05-28
I remember playing this a little while back. Good RTS game, but without the music and the cutscenes to be able to tell what the hell you're supposed to do in the mission, it isn't quite the same. Half the fun now seems to be trying to figure out what the mission objective is. Still a good game though.

---

### Post by 23meg on 2005-05-28
so are the music and the sound fx totally absent from this version? i can't seem to get them working.

---

### Post by apollyonis on 2005-05-28
Sound FX are there. Make sure to install libsdl1.2debian-all under synaptic.

---

### Post by 23meg on 2005-05-28
installed, still no sound. when i set the sound fx slider to max, it just returns back to zero once i come back to the dialog. any config lines i have to edit somewhere that you know of?

---

### Post by dolny on 2005-05-28
They will add cutscenes, network play etc. 
They don't know how to reverse-engineer the cutscenes right now... maybe if they won't be able, a text briefing would be some solution. Anyway, they're working on the netcode atm. 

PS. Sorry, I can't help you. Maybe ask at their forums...dunno. Google.

---

### Post by 23meg on 2005-05-28
btw, how exactly do you launch the game? it only runs when i double click warzone.sh; i can't execute that script from the terminal, and can't execute the binary itself in any way.

---

### Post by dolny on 2005-05-29
I just used: ```
./thenameofthebinary
``` or ```
sh thenameofthebinary
```

---

### Post by nivenmk1 on 2005-05-30
Anyone else getting  this:
```
nivenmk1@ubuntu:~/Desktop$ sh warzone.2100_rev86-english.run
Verifying archive integrity... All good.
Uncompressing Warzone 2100 rev86-english Installer.............................. .........................
/home/nivenmk1/.setup17020: error while loading shared libraries: libgtk-1.2.so. 0: cannot open shared object file: No such file or directory
```

or this

```
nivenmk1@ubuntu:~/Desktop$ ./warzone.2100_rev86-english.run
bash: ./warzone.2100_rev86-english.run: Permission denied

```

when trying to install?

Checked for libgtk with synaptic and have the common package.  Other than that me and my immensely finite knowledge are rather stuck.

---

### Post by dolny on 2005-05-30
```
nivenmk1@ubuntu:~/Desktop$ ./warzone.2100_rev86-english.run
bash: ./warzone.2100_rev86-english.run: Permission denied
```

Under console: 

```
sudo chmod 777 warzone.2100_rev86-english.run
```

I'm a newbie, but:

```
/home/nivenmk1/.setup17020: error while loading shared libraries: libgtk-1.2.so. 0: cannot open shared object file: No such file or directory
```

You can try installing gtk 1.2 on the system also.
Good luck.

---

### Post by slux on 2005-05-30
[QUOTE=apollyonis]In the readme it says under "ToDo" Network stuff so I'm presuming that Loki never got networking, hence multiplayer, to work. Sorry. I'd like to play this on multiplayer too.  :neutral:[/QUOTE]

This doesn't have anything other than the installer (which I think is used even by ID software for installs on Linux) to do with Loki Games. :)

The game was GPLed and work is still probably going on with the networking so you might be able to do that in the future. :)

---

### Post by dolny on 2005-05-30
Yeah, they're working on it right now. The highest priority I think = netcode. Woohoo :)

---

### Post by dolny on 2005-06-20
Netcode works.

> How's the network code stuff going? When will we be able to kill our friends through the net?

Killing your friends through the net is not possible and not planned
anyway, but you can play warzone through the net ;)

Available stuff is in the download section at berlios.
[http://developer.berlios.de/project/showfiles.php?group_id=2909&release_id=6176](http://developer.berlios.de/project/showfiles.php?group_id=2909&release_id=6176)

This is a test version but it's pretty usable.

---

### Post by dolny on 2005-06-20
I can't compile it, can anybody backport it?

---

### Post by -Rick- on 2005-06-20
I played this game on the psx before :) Cool that it has been ported to linux.

BTW: I remember that you could take control of a unit and ride with it...is this still possible?

---

### Post by dolny on 2005-07-07
A version with multiplayer is now available at: [http://www.liflg.org/?catid=6&gameid=63](http://www.liflg.org/?catid=6&gameid=63)

---

