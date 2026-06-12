---
title: "compiz by default on both monitor (nvidia twinview)"
date: 2008-01-11
forum: Desktop Effects &amp; Customization
---

### Post by ^Albe^ on 2008-01-11
hi to all, i have a little problem
nvidia agp card connected to my "first" default monitor and to a lcd television

all running and configured in twinview

the problem:
i have compiz called by "sessions" in the gutsy menu, but in the second monitor-out (the tv) compiz does not starts and so i have no border at all around the windows (non chance to close/minimize/maximize)
so i thinked about to launch a compiz session from the terminal in the second monitor, and it works!
the problem: how to launch, from sessions, compiz on both the monitor by default?

regards and thx for any suggestion

---

### Post by kryth on 2008-01-12
use this script in your start up

#!/bin/bash
sleep 2
DISPLAY=":0.0" /usr/bin/compiz --replace ccp --sm-disable --only-current-screen &
DISPLAY=":0.1" /usr/bin/compiz --replace ccp --sm-disable --only-current-screen &
DISPLAY=":0.0" /usr/bin/emerald --replace &
DISPLAY=":0.1" /usr/bin/emerald --replace &

make sure to disable whatever else you had starting up compriz...
you can always just cut and paste that into termal first to see if that fixes the problem...
wish i could explain it better but too little sleep and too much wine.

---

### Post by ^Albe^ on 2008-01-12
works! 
thx for the help

---

