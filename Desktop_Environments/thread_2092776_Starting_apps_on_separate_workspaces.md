---
title: "Starting apps on separate workspaces"
date: 2012-12-08
forum: Desktop Environments
---

### Post by dcollins on 2012-12-08
Invariably the first thing I do after I log in to a KDE desktop is start a bunch of apps using kstart, using --desktop to send them to separate workspaces.

This seems to work fine from the command line, but if I try to launch them from a bash script all the applications start
on the same workspace as my terminal. For example, 

--------------

#!/bin/bash

echo "Starting apps..."

kstart --desktop 1 firefox &> /dev/null &
kstart --desktop 2 kontact &> /dev/null &
kstart --desktop 3 dolphin &> /dev/null &
kstart --desktop 4 konsole &> /dev/null &

--------------

I'm just curious why this doesn't work the way I expect, and if there is a simple alternative that might work better.

---

### Post by Jakin on 2012-12-15
How about trying this the GUI way- and there are 2 ways (see the images below).

Under the Application settings goto: Size and Position> Desktop "force" and choose which desktop you want this application to always appear, and of course you can add more than one setting per app- maybe the pixel position on said desktop, or the window size, ect. 
Thats the quickest way- but you can also do this from KDE control panel "window rules" where you would also remove the rules you no longer need.

This seems to work for me, and KDE remembers at each boot. Hope it helps :)

---

### Post by Merrattic on 2012-12-15
Alternatively:

wmctrl

devilspie

---

### Post by dcollins on 2012-12-15
The application settings method looks to be a great solution for me. Thank you so much for your help!

---

### Post by Jakin on 2012-12-15
> **dcollins said:**
> The application settings method looks to be a great solution for me. Thank you so much for your help!

You are quite welcome :)

---

