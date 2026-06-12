---
title: "Lost progs... where are they?"
date: 2006-01-12
forum: Desktop Environments
---

### Post by avantgardaclue on 2006-01-12
Hi guys, total convert here, ubuntu running smoothly with very little to complain about!

HOWEVER! I have downloaded/installed many progs from synaptic and automatix, some of them show in my application menus some have disappeared into the entrails of my computer, probably never to be seen again unless one of you kind souls is able to help me locate them and add them to the menus. Downloaded but never to be seen are wordpress and scribus. Using automtix i downloaded some prog (name's gone) that is meant to list every prog on the computer, now isn't it ironic that that too never managed to get added to the menus!

cheeers.... Simon the total convert!

---

### Post by schilcha on 2006-01-12
Only some programs are added to the applications-menu. All the others, you have to add manually or start via the command line. 

If you're looking how to start a program, look up the installed package in synaptic and open its properties (try a right-click on the package and select properties from the popup menu). There's a tab that contains all files installed with that package. Some of them are executabel files -- ususaly  in some /path/ending/with/bin/). 

If you then right-click on the gnome-applications-menu, you can select to edit the menu. Add a custom entry pointing to the executable file.

Good Luck!

---

### Post by Alpha_toxic on 2006-01-12
Try finding them using the command line. Most programs are started by a command that is the same as the name of the package it was in when you installed it (actally both the package and the command are usually named after the program). Like OpenOffice is started by [COLOR="Red"]openoffice[/COLOR] and XMMS by [COLOR="Red"]xmms[/COLOR].
When you find the exact commands of the progs you're looking for, it should be easy to add them to the menus.
NOTE: in the conslole, writing something and then pressing TAB a few times (2 I guess) will give you a list of all commands that start with this something.

---

### Post by daschl on 2006-01-12
if you want to add them to the menu, run the menu editor :)

if you want to find the executable path run this command:

```

$find / -name [PROGNAME] 2> /dev/null

```

then you will - hopefully - find something that looks like /usr/bin/programmname 

some icons could be found in /usr/share/pixmaps

hth

---

### Post by avantgardaclue on 2006-01-12
Thanks for the replies guys. the command line stuff sort've went over my head a bit but i'll persevere as i'm sure it'll be educational for me!!

$find / -name wordpress 2> /dev/null 
or 
$find / -name scribus 2> /dev/null 

in terminal did nothing but return to the prompt... maybe i was doing something wrong.

However i used file browser to go down to /usr/bin/ and found scribus, double clicked and up came the prog... brilliant. So i right clicked on the gnome-applications-menu selected office (to where i was going to add scribus) and saw that it was in fact already there AND ticked, so i closed the menu editor opened the office menu, but no scribus there, so reopened menu editor unticked and then re ticked scribus, closed, went back and there she was... hooray!

Having regard to wordpress, i can, indeed, find lashings of wordpress files but not the executionable: /usr/share/wordpress

Strange... thanks for your help.... Simon

---

### Post by bagel on 2006-01-12
Hello there;

Can you execute wordpress from the command line? If yes, then the easiest way to find the exact location of the executable is:

```
whereis [COMMAND_TO_RUN_PROG] 
``` for example:

```
whereis wordpress
```

Hope to help,
Ciao, 
bagel

---

### Post by Thirsteh on 2006-01-12
Or type 'sudo updatedb', when it's done type 'locate wordpress'.

---

### Post by hillbilly on 2006-01-12
More often than not, you can locate your executable under /usr/bin/. And the name of your executable is the name of the program you installed. Like for example if the program you selected from synaptic is xmms, then the program would be available as xmms and so on.

So now once you have this name then just type this in a terminal and hit enter
> $/> xmms

If this runs, that means the executable is located in one the locations set in your PATH variable. So now to find what the location is > $/> whereis xmms
This will return the location of the app (in this case xmms).

Now if this doesnt return anything relevant. Then just use find
> $/> find / -name xmms  2>/dev/null

If this still doesnt return the path, that means the name you are searching for is incorrect. So just use wild cards while searching.
> $/> find / -name *xmms* 2>/dev/null

now if this too doesnt give you an output, then that means you  havent installed the app ;)

---

### Post by cwaldbieser on 2006-01-12
Here is a quick script that will list all the commands installed, given a package:

```

#!/bin/bash

#############################################################
# Prints out a list of all the executable files installed for
# the package name given.
#############################################################

dpkg -L "$1" | xargs -n 1 | { while read FNAME; do if [ ! -d "$FNAME" ]; then if [ -x "$FNAME" ]; then echo "$FNAME"; fi; fi; done; }

```
Usage is "$ <script-name> <package-name>".

---

