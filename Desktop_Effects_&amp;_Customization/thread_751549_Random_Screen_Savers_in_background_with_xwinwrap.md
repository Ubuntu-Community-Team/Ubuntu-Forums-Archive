---
title: "Random Screen Savers in background with xwinwrap"
date: 2008-04-10
forum: Desktop Effects &amp; Customization
---

### Post by protorox on 2008-04-10
In order to use xwinwrap to randomly choose a screensaver to run at Gnome start up...

You must first save a file listing of screensavers to a file (i.e. "ss.list").

Example:
```

find /usr/lib/xscreensaver/* > ss.list

```

Finally, you then run this script (randSS.sh) at startup:
```

#!/bin/bash

# First, kill xwinwrap if already running
killall xwinwrap

# Obtain the number of screensavers in list
RANGE=`wc -l ss.list|cut -d' ' -f1`

# Create a random number within the range
SSnum=$RANDOM
let "SSnum %= $RANGE"

# Choose the random screensaver to run
SS=`head -$SSnum ss.list | tail -1`

# Run xwinwrap with this screensaver
xwinwrap -ni -argb -fs -s -st -sp -nf -b -- $SS -window-id WID &  

```

**This will also work with randomly selecting videos to play with mplayer!** :)

One more idea! : You can also schedule this script with cron to constantly change the screensaver running in the background!

Your truly,
PRoTo RoCKer

---

### Post by overdrank on 2008-04-10
Hi and will try it out here soon. :)

---

