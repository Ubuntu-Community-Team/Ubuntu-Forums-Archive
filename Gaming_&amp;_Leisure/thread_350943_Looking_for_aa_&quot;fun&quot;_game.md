---
title: "Looking for aa &quot;fun&quot; game"
date: 2007-02-01
forum: Gaming &amp; Leisure
---

### Post by acorn22 on 2007-02-01
I am looking fo a "fun" game for 2 or 3 people to play via lan or internet. Preferabley multi-latform (mac+linux), but not needed.

By fun I just mean a game that is easy to play, and not 'hardcore' per se. Warcraft 2 and 3 are good examples of what I mean.

I'm trying to find a good game for my dad and brother to play, and we've exausted warcraft ;)

Any ideas? (any genre, really)

---

### Post by siman on 2007-02-01
I'm also into RTS and recently found Galcon .. multiplatform and got a 3 day trial, multiplayer of course, even got at least 2-3 servers online any time

[http://www.imitationpickles.org/galcon/index.html](http://www.imitationpickles.org/galcon/index.html)

everyone who's at least a bit into strategy got hooked after 2 games :-) tell me how you like it

---

### Post by Spyder_23456 on 2007-02-01
Can you download emulators for the linux system? I got a few on my Windows XP, but will they still work for linux?

---

### Post by TrendyDark on 2007-02-01
Antoher fun, Linux-native game is Enemy Territory.

I admin an Enemy territory server, so if you want, install enemy territory, and once you're in the game hit the ~ button to drop down the console then type:

/connect etpub.khbclan.com 

You'll be at our server :)

---

### Post by siman on 2007-02-01
yes ET forever :-) but galcon is definitly the least hardcore

emulators: which are you using? mame works under ubuntu .. there are a couple of emus in the repository

---

### Post by EvilMarshmallow on 2007-02-01
If you enjoyed Warcraft 2 & 3, you'll probably like Battle For Wesnoth.

It's in the repos... just discovered it myself this week and wow, I'm going to waste a lot of my life there over the next few weeks!

---

### Post by hikaricore on 2007-02-01
> **Spyder_23456 said:**
> Can you download emulators for the linux system? I got a few on my Windows XP, but will they still work for linux?

[http://linuxemu.retrofaction.com/](http://linuxemu.retrofaction.com/)

---

### Post by Naegling23 on 2007-02-01
I would recommend some of the earlier shooter type games.  The quake 3 style run and gun is pretty fun, and not too complex.  There are a bunch of open source games based on this style like nequiz (sorry spelling) that you might want to check out.  You can also give ut2004, and soon to be released 2007 a shot, they have different play modes from the basic shoot everyone, to more tactical dumbed down battlefield type stuff.  Most of these games are relatively simple, you dont need more than a handlfull of keys, and can be pretty fun.

---

### Post by acorn22 on 2007-02-01
```
lowell@ubuntu:~/Desktop/galcon$ ./galcon 
/home/lowell/Desktop/galcon/galcon/main.py:546: RuntimeWarning: use font: libSDL_ttf-2.0.so.0: cannot open shared object file: No such file or directory
Please install SDL_ttf.
lowell@ubuntu:~/Desktop/galcon$ 

```

??

---

### Post by hikaricore on 2007-02-01
> **acorn22 said:**
> ```
lowell@ubuntu:~/Desktop/galcon$ ./galcon 
/home/lowell/Desktop/galcon/galcon/main.py:546: RuntimeWarning: use font: libSDL_ttf-2.0.so.0: cannot open shared object file: No such file or directory
Please install SDL_ttf.
lowell@ubuntu:~/Desktop/galcon$ 

```

??

```
sudo aptitude install libsdl-ttf2.0-0
```

:)

Should install libsdl-ttf2 and any other libs needed by libsdl-ttf.

---

### Post by acorn22 on 2007-02-01
> **hikaricore said:**
> ```
sudo aptitude install libsdl-ttf2.0-0
```:)

Should install libsdl-ttf2 and any other libs needed by libsdl-ttf.

Thank you so much !

This game is exactly what I was looking for. Is there any way at get three people playing?

---

### Post by siman on 2007-02-02
> 
Is there any way at get three people playing?


what do you mean? you can play online vs people if you click "net game" ( i think) ... should be plenty of servers. there is no extra LAN mode, if that is what you meant

---

### Post by acorn22 on 2007-02-02
I hadn't played when I asked.

But yeah that game is addicting!

ps- Any other suggestions. This game is fun, but not for a marathon :P

And I tried Wesnoth and that is fun. I never knew it was multiplayer

---

### Post by LordFu on 2007-02-04
I've been playing a ton of Toribash. It's fun and multiplayer.

---

### Post by 3rdalbum on 2007-02-05
Overkill is a bit of a laugh, and it can be played over a LAN.

---

### Post by szantaii on 2007-09-21
0verkill is a fun game and it's in the repositories. We usually play it over Internet. It's sad that the game's server and bots are a bit unstable, so I've written a litlle script so we can play. If the server or the bots quit the scripts restart them in 3 secs, so you just have to reconnect yourself in the game, and continue playing.

overkill-start.sh:
```
#!/bin/bash

#overkill-start.sh 2007-09-21
#
#script usage:
#			./overkill-start.sh <port> <number of bots>
#
#	example:	./overkill-start.sh 6666 5
#
#do not modify anything under this line
#--------------------------------------

overkill-server -n -p $1 &

sleep 3

for i in `seq 1 $2` ;
do
	overkill-bot -a 127.0.0.1 -p $1 &
done

while [ 1 ] ; 
do
	sleep 3
	ps -C overkill-server
	if [ $? -eq 0 ]
	then
		ps -C overkill-bot
		if [ $? -ne 0 ] ;
		then
			for i in `seq 1 $2` ;
			do
				overkill-bot -a 127.0.0.1 -p $1 &
			done
		fi
	else
		killall overkill-bot
		sleep 1
		overkill-server -n -p $1 &
	fi
done

exit 0


```

overkill-stop.sh:
```
#!/bin/bash

killall overkill-start.sh
if [ $? -eq 0 ]
then
	echo "overkill-start.sh killed"
fi
killall overkill-bot
if [ $? -eq 0 ]
then
	echo "overkill-bot(s) killed"
fi
killall overkill-server
if [ $? -eq 0 ]
then
	echo "overkill-server killed"
fi

exit 0


```

Save them, and to get the scripts working you have to chmod +x them. That's all, you can play now. :D

---

### Post by Gwarkill on 2008-03-08
Woot Toribash All the way!

---

### Post by Sockerdrickan on 2008-03-08
[http://www.teewars.com/](http://www.teewars.com/)

---

