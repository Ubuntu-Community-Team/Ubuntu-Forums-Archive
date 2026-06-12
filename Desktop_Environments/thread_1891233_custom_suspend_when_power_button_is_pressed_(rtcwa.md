---
title: "custom suspend when power button is pressed (rtcwake)"
date: 2011-12-05
forum: Desktop Environments
---

### Post by jackobean on 2011-12-05
Hi

I've been trying to figure out how to override the gnome suspend behaviour under oneiric with a custom script that uses rtcwake. That is when i press my 'power' or 'suspend' buttons or click suspend in the pm applet i want the following script to run rather than the normal shutdown/suspend behaviour.

```
suspenduntil.sh 13:00
```

where suspenduntil.sh looks like this:
```
#!/bin/bash

# Suspends the machine until the next occurence of the time given as input

if [ -z $1 ]; then
	echo  "syntax: suspenduntil.sh <time>"
	exit
else
	WAKETIME=$1
fi

WAKETIMEEPOCH=$(date --date="$WAKETIME" +%s)

#If the current time is already after WAKETIME then wakeup tomorrow
if [ $(date +%s) -gt $WAKETIMEEPOCH ]; then
        WAKETIMEEPOCH=$(date --date="tomorrow $WAKETIME" +%s) 
fi

sudo rtcwake -u -m mem -t $WAKETIMEEPOCH

```

and I've googled around a bit without much luck. Any ideas?

---

