---
title: "Problem with Conky start up shell (not a sleep issue)"
date: 2011-03-18
forum: Desktop Environments
---

### Post by zookrider on 2011-03-18
I have a shell script used to start my conky on start up:
```
#! /bin/bash
sleep 20 &&
conky -c ~/Conky/conkymain &
```
which works just fine with one exception. In my conkymain file I have the following:
```
${color2}${execpi 30 todo.sh -p ls }
```
which obviously launches my text based to do list. When I launch conky using the above shell the area where my to do list should be is blank, but if I launch conky from the command line using:
```
conky -c ~/Conky/conkymain
```
which is the exact same code as is in the shell script, then the to do list shows up perfectly. It doesn't matter if the shell is launched by Startup Application Preferences or just by double clicking it, the to do list won't show up. This makes no sense to me and several hours of googling have yielded no answers.

---

### Post by zookrider on 2011-03-19
Ttt

---

