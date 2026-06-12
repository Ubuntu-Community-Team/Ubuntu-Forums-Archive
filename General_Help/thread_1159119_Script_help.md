---
title: "Script help"
date: 2009-05-14
forum: General Help
---

### Post by PureLoneWolf on 2009-05-14
Hi all

I wonder if anyone can help me.  I am running XBMC on a dual-monitor setup.  I like to have it maximised to full screen on my main monitor and still be able to work in monitor 2.

I found a script for boxee that uses wmctrl to do this and the wmctrl command line works perfectly, but I would like the script to launch xbmc, wait a couple of seconds and then execute the wmctrl command.

This script worked perfectly when I was using boxee, but I got rid of boxee due to performance issues.

Here is the original boxee launch script:
```

#! /bin/bash

STATUS=0
WINCLASS=Boxee.Boxee
DISPLAY=:0.0
SLEEPDELAY=5


/opt/boxee/run-boxee-desktop "$@" & 

while [ $STATUS -eq 0 ]
do
  sleep $SLEEPDELAY
  STATUS=`wmctrl -x -l | grep $WINCLASS | wc -l | awk '{print $1}'`
done

wmctrl -x -r $WINCLASS -b toggle,fullscreen

```

If I run the following command XBMC maximises on the correct screen as I would like:
```

wmctrl -x -r XBMC Media Center.XBMC Media Center -b toggle,fullscreen

```

I tried to modify the boxee script to this
```

#! /bin/bash

STATUS=0
WINCLASS=XBMC Media Center.XBMC Media Center
DISPLAY=:0.0
SLEEPDELAY=5


/usr/bin/xbmc "$@" & 

while [ $STATUS -eq 0 ]
do
  sleep $SLEEPDELAY
  STATUS=`wmctrl -x -l | grep $WINCLASS | wc -l | awk '{print $1}'`
done

wmctrl -x -r $WINCLASS -b toggle,fullscreen

```

When I run this, XBMC loads windowed as expected, but then the wmctrl line seems to be ignored.  I tried increasing the delay to 10 seconds just in case, but as XBMC launches considerably quicker than boxee, I wouldn't think this is the issues.

If anyone could assist it would be great..apologies if this is in the wrong forum.

Thanks

---

### Post by jonobr on 2009-05-14
hey

TRy posting over in programming,
the post there move a lot slower and people there are excellent.

---

### Post by PureLoneWolf on 2009-05-14
I'll do that - Thanks :)

---

