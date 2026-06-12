---
title: "Shell Script question"
date: 2005-07-13
forum: Desktop Environments
---

### Post by leezer3 on 2005-07-13
Hi guys,
Very simple question, but I know next to nothing about shell scripts. Anyway, I've got a game (Simutrans, latest devel version) for which the only way to launch it is to do this in a terminal:
```
cd /home/christopher/simutrans
./simutrans 
```
Just typing simutrans into run doesn't work, and this means that I want a simple little shell script to fufill this function. (The script should boot up & run in a terminal, please :) ) 

Thanks

-Leezer-


WE HAVE INTERNET  \\:D/  IN UBUNTU!!!

---

### Post by poptones on 2005-07-13
The "cd" command just tells your command line to go to that directory. In linux you have to give a full path to any program not in your default path even if it's a program in the same directory. That's why you put the ./ before the program name. The dot "." means "this directory" (just like windows) so "./foo" means "run program foo in this current directory."

You can separate commands on one line with a semicolon ";"

So... you can do the same thing you are doing on those two lines above by typing this:

cd /home/christopher/simutrans;./simutrans

If you want to make a launcher you can do this by right clicking on your desktop, selecting "make launcher" and entering the single line above into the "command" box. Click the box "run in terminal." Give it any name you like, select an icon, and off you go...

---

### Post by leezer3 on 2005-07-13
[QUOTE=poptones]The "cd" command just tells your command line to go to that directory. In linux you have to give a full path to any program not in your default path even if it's a program in the same directory. That's why you put the ./ before the program name. The dot "." means "this directory" (just like windows) so "./foo" means "run program foo in this current directory."

You can separate commands on one line with a semicolon ";"

So... you can do the same thing you are doing on those two lines above by typing this:

cd /home/christopher/simutrans;./simutrans

If you want to make a launcher you can do this by right clicking on your desktop, selecting "make launcher" and entering the single line above into the "command" box. Click the box "run in terminal." Give it any name you like, select an icon, and off you go...[/QUOTE]
 Hi there,
Sorry to dissapoint you, but this doesn't work :(
What I get at the moment is a flash of terminal, and then back to the desktop.

Some more info on this app: It needs the terminal to be running in the background at all times, as this is what it uses to output messages etc. This is why I felt that I needed a shell script to execute the terminal and then the proggie.

Thanks for your help

-Leezer-

---

### Post by alastair on 2005-07-13
Even an "alias" would help here.

Just try, in a shell :

alias simu='cd /home/christopher/simutrans; ./simutrans'

Then run by typing "simu" (and you can add to your ~/.bashrc say).

If you want to have a shell script, you will need to start "gnome-terminal" probably, and execute the above inside it e.g. a launcher to :

gnome-terminal  -e /home/christopher/simutrans/simutrans

---

### Post by leezer3 on 2005-07-13
[QUOTE=alastair]Even an "alias" would help here.

Just try, in a shell :

alias simu='cd /home/christopher/simutrans; ./simutrans'

Then run by typing "simu" (and you can add to your ~/.bashrc say).

If you want to have a shell script, you will need to start "gnome-terminal" probably, and execute the above inside it e.g. a launcher to :

gnome-terminal  -e /home/christopher/simutrans/simutrans[/QUOTE]
 That's slightly better, but the terminal still closes before the game has a chance to do anything :(

Thanks

-Leezer-

---

### Post by alastair on 2005-07-13
OK - not sure what the problem is - the terminal should only exit once the command "-e" executed exits ...

So .... since it's only a game, I'd live with the "simu" alias, or even (heaven help me) the :

cd ~/simutrans; ./simutrans

Big deal. Alternatively, do some digging ... you might learn something, even if it turns out to be irrelevant to anything except playing "simutrans" ...

---

### Post by wylfing on 2005-07-13
Do this:
1. Make a file called simu.sh in your home directory. The contents of the file should be:```
#!/bin/bash

cd /home/christopher/simutrans
./simutrans
```
2. Make this file executable with ```
chmod u+x simu.sh
```
3. Make a new launcher (on your taskbar or the desktop) that runs the command
```
gnome-terminal -e /home/christopher/simu.sh
```

---

### Post by leezer3 on 2005-07-14
[QUOTE=wylfing]Do this:
1. Make a file called simu.sh in your home directory. The contents of the file should be:```
#!/bin/bash

cd /home/christopher/simutrans
./simutrans
```
2. Make this file executable with ```
chmod u+x simu.sh
```
3. Make a new launcher (on your taskbar or the desktop) that runs the command
```
gnome-terminal -e /home/christopher/simu.sh
```[/QUOTE]
 Precislely what I was looking for!
(Never new it could be so simple :P)

Thanks :D

-Leezer-

---

