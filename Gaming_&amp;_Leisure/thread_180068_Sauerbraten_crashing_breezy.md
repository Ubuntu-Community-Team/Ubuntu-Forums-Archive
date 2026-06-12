---
title: "Sauerbraten crashing breezy"
date: 2006-05-21
forum: Gaming &amp; Leisure
---

### Post by whatrucrazy on 2006-05-21
Sauerbraten has managed to freeze my system 3 times now, requiring a full reboot. has anyone else had this issue? am also using cube but have had no probs at all with that engine.
just curious, can keep using cube as there is no too much difference but would like to know what the go is with Sauerbraten.

---

### Post by odelay on 2006-10-01
Yeah...Sauerbraten has crashed my computer 2 out of 2 times.  I haven't played the original Cube, I just assumed Cube 2 would have much better graphics.

When I get a chance, I'm going to also check out Nexuiz and Warsow.

---

### Post by Rhubarb on 2006-11-08
Sauerbraten works fine for me on Dapper and Edgy.  Have got an nVidia card if that makes any difference.

---

### Post by Hacim on 2006-11-09
yes it has lockup dapper for me several times but don't reboot just do a CTRL+ALT+BACKSPACE and log back in.I havent had it happen when I just run the client derectly though (i.e. bin/linux_client) vs using the shell script perhaps it sets some varibles wrong or something.It also locksup on windose (compiled from source).

That been said play more CUBE2.

---

### Post by aidanr on 2006-11-09
i had sauerbraten lock up on me today, but i just switched to another tty and killed the process to get out of it, i haven't looked into it further yet

---

### Post by misfito on 2006-11-12
I'm using ubuntu dapper drake, when I try to run sauerbraten_unix the screen goes black for a few seconds and then it returns to the previous window where the file is, but with the resolution changed and the mouse not working at all.

/home/Desktop/sauerbraten/bin_unix
/home/Desktop/sauerbraten/CVS
/home/Desktop/sauerbraten/data
/home/Desktop/sauerbraten/docs
/home/Desktop/sauerbraten/packages
/home/Desktop/sauerbraten/src
/home/Desktop/sauerbraten/README.html
/home/Desktop/sauerbraten/sauerbraten_unix

Do any 1 knows if I'm missing something?

---

### Post by Rhubarb on 2006-11-12
That's all the files you need there misfito, when you run the game some extra cfg's should appear (config.cfg, servers.cfg if you play online).

I made up a shell script to lauch sauerbraten:
```
cd /home/hp/sauerbraten/
echo "*********************************************************************************" >> game.log
echo "" >> game.log
echo "" >> game.log
echo "" >> game.log
echo "Starting Sauerbraten..." >> game.log
date >> game.log
./sauerbraten_unix -w1280 -h800 >> game.log
```
You'll have to make sure that 3d acceleration is working properly (I can't remember how to check, but it's floating around the forums here somewhere).

---

### Post by gymsmoke on 2006-11-24
Not exactly on topic, but i'm having problems getting the game to initialize.  I get an error related to the sdl library.  i've installed sdl-debian (1.2), and sdl-debian-alsa, but it hasn't changed.  Am I missing something else?
(running Dapper)

---

### Post by Hacim on 2006-11-25
I think you're missing sdl-mixer,other wise posting the actual output of Sauerbraten would be a help.

---

