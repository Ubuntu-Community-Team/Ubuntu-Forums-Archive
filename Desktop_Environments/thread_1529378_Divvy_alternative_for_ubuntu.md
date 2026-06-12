---
title: "Divvy alternative for ubuntu"
date: 2010-07-12
forum: Desktop Environments
---

### Post by Dooley on 2010-07-12
Hey all,

I was just wondering if something similar to [divvy]("http://www.mizage.com/divvy/") for mac exists. My googling couldn't find anything.

Thanks,
Dooley

---

### Post by diesch on 2010-07-12
You can write shell scripts. This one resizes the currently active window the 66% width and full height:  

```

#!/bin/sh

set -- $(xwininfo -root| awk -F '[ :]+' '/ (Width|Height):/ { print $3 }')
width=$1
height=$2

wmctrl -r :ACTIVE: -e 0,0,0,$((width*2/3)),$height

```

This one lets you click two windows and then resizes them so that each has half the screen:

```
#!/bin/sh

set -- $(xwininfo -root| awk -F '[ :]+' '/ (Width|Height):/ { print $3 }')
width=$1
height=$2

win1=$(xwininfo| awk '/^xwininfo: W/ { print $4 }')
win2=$(xwininfo| awk '/^xwininfo: W/ { print $4 }')

wmctrl -i -r $win1 -e 0,0,0,$((width/2)),$height
wmctrl -i -r $win2 -e 0,$((width/2)),0,$((width/2)),$height
```

---

### Post by Dooley on 2010-07-14
Interesting idea, how I'd really not have to go to the command line to do window management.

I'll try fire a few system shortcuts in and see if it works.

Thanks again.

---

### Post by srf21c on 2010-11-30
Another Divvy user here that recently switched back to Ubuntu from Mac OS X.  

You might want to [[COLOR="Blue"]check out Grid plug-in for Compiz[/COLOR]]("http://www.webupd8.org/2009/12/linux-w-compiz-tile-position-and-resize.html").  Grid is included by default in recent versions of Ubuntu.

---

### Post by snoxu on 2011-01-07
I was wondering the same thing as the OP.

Had a look at Compiz's Grid.

It's decent but not really as good as Divvy because it's grid allows for smaller windows and in different places on the desktop.

---

