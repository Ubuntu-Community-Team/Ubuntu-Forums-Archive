---
title: "running a sauerbraten server"
date: 2006-08-26
forum: Gaming &amp; Leisure
---

### Post by oldmanstan on 2006-08-26
i have having issues with the sauerbraten dedicated server. whenever i run the server it starts just fine and players can connect but then when i want to stop the server i hit ctrl-c and nothing happens. i end up having to stop the process manually.

also, does anyone know of a faq or something for the server? because it really isn't documented that well, or do i just have to mess with it until i get the options right?

thanks

---

### Post by Onimae on 2006-09-04
I'm having the same problem, well, the fact that it's not very well documented. What you can do to stop the server is push "ctrl+z". That's the sequence for the what's called the escape key. It'll stop any process that you're running in the terminal. I would, however, like to know where I can find information on running a dedicated server, because the only thing I can figure out how to do is run it with default settings (whatever those are).

**Onimae**

---

### Post by Onimae on 2006-09-05
Okay, after a bit of mucking around and looking at the readme that comes with the game I've made some discoveries.

First off, the server is obviously run by invoking ./sauerbraten_unix -d. However, there are some other useful command line options you have. -pPASS will set the admin password to PASS. To log in as the admin (or "master" as the game calls it), go into your server and type /setmaster 1, and if someone else has already taken master, but you want it, type /setmaster 1 PASS. 

While you are the master you can do a few things. /kick, does what it says. You can also set the "master mode" of the game, by invoking /mastermode X, where X is an integer between 0 and 3. 0 is "free mode", where the only power the master has is to kick people. 1 is "veto mode", where the master reserves the right to change the map and game type, without a vote. 2 is "spectator mode", where any new players to join the game will become spectators. The master is the only one who can switch them out of spectator mode. The final type, type 3, is private mode, where no new users will be accepted into the game.

There are also two other useful command line options you can use: -cX and -nNAME. -c will set the maximum clients to X. -n will set the description of the server to NAME. 

That's about all i've found.

**Onimae**

---

### Post by patrick295767 on 2007-11-19
hi, 

by the way how can we change / set the map of dedicated server ?

```
./sauerbraten_unix -lbase/rpg_01 -d
```
not working

```
./sauerbraten_unix -lbase/rpg_01 
```
working as non-server

---

### Post by donarntz on 2009-12-18
Is there a gui interface for the sauerbraten server?

---

### Post by calin rusu on 2011-03-20
Usually Ctrl+C will shut down the server.
If it doesn't do that, try running the server in background without keeping a terminal open. Assuming that your sauerbraten dirrectory is in your home directory:

cd ~/sauerbraten
nohup ./bin_unix/linux_server &

after that you can hit Ctrl+D to close the terminal and server will keep running in the background.

To stop you can do:

cd ~/sauerbraten/bin_unix
killall linux_server

or

list all running processes with 

ps -A

and kill your sauer server by pid (take the pid from ps -A output)

sudo kill -9 <pid>

---

