---
title: "shortcuts?"
date: 2006-01-05
forum: Gaming &amp; Leisure
---

### Post by M3lted on 2006-01-05
hi guys 
im new to linux and really like this distro.
iv been playing with synaptic to install some simple game's.
most of the games and app's are getting a shortcut in the menu
but for some game's they dont get created.
for excample ,epiphany, i installed it but i cant seem to find it. 
could any of u guys would b so kind to explain me why , and how i can fix this plss :D.

Cheers

---

### Post by Perfect Storm on 2006-01-05
Epiphany is a browser ;). If it don't show up try with **killall gnome-panel** and see if it helps. If a game don't have a shortcut open the terminal and write the name of the game should do the trick (eg. Dominions 2 game you just type dom2 in the terminal to start it). When you find out which command start the game you can make a launcher for it or add it to the application tab. There you have the oppotunity to put the command to it, name annd Icon.

---

### Post by M3lted on 2006-01-05
but synaptic say's epiphany is a boulderdash 2 clone :S lol
a well thx for the info :)

---

### Post by jrib on 2006-01-05
The epiphany package in synaptic is a game (I've never tried).  For the browser, the pacakge is epiphany-browser.  To try to figure out the bin for the game you can try the following:

```
dpkg -L epiphany | grep bin
```

I think the above works, but I'm not on a *nix machine to make sure.  Just look for a file you can run that is in a bin folder. Try to get the man page (man <command>) or run it with -h (<command> -h) to see if you can get some help.

[e] since you are new, I'm not sure if you are comfortable with using Accessories->Terminal where these commands should be inputted.  Here is a good tutorial: [http://linuxcommand.org/](http://linuxcommand.org/) .

---

### Post by Perfect Storm on 2006-01-05
ops, my fault. Sorry.

---

### Post by M3lted on 2006-01-05
[QUOTE=_jason]The epiphany package in synaptic is a game (I've never tried).  For the browser, the pacakge is epiphany-browser.  To try to figure out the bin for the game you can try the following:

```
dpkg -L epiphany | grep bin
```

I think the above works, but I'm not on a *nix machine to make sure.  Just look for a file you can run that is in a bin folder. Try to get the man page (man <command>) or run it with -h (<command> -h) to see if you can get some help.

[e] since you are new, I'm not sure if you are comfortable with using Accessories->Terminal where these commands should be inputted.  Here is a good tutorial: [http://linuxcommand.org/](http://linuxcommand.org/) .[/QUOTE]


thx for the tutorial,thats a good way to start :)
iv been fiddeling around with the terminal , but i get so much wiser, when i know what im actually doing :)

---

