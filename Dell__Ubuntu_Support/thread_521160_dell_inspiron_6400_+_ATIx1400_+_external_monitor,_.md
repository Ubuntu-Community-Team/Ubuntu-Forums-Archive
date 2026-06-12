---
title: "dell inspiron 6400 + ATIx1400 + external monitor, crt1"
date: 2007-08-09
forum: Dell  Ubuntu Support
---

### Post by bash4fun on 2007-08-09
hy everybody!
yesterday i found out how to get my external monitor to work with my dell laptop and ubuntu. i added 2 rows in my xorg.conf und used the "aticonfig --enable-monitor=crt1" command to switch to my external monitor using the terminal. 

```
In Section Device:

Option "ForceMonitors" "lsdv,crt1"
Option "EnableMonitor" "lsdv,crt1"

```

is it possible that this doesn't work with beryl and xgl enabled?

---

### Post by cypherl0k on 2007-08-13
I highly suggest you read this thread.
It may answer most if not all your questions on this.
[http://ubuntuforums.org/showthread.php?t=301941]("http://ubuntuforums.org/showthread.php?t=301941")
I'm using a Optiplex GX620+x600 - and helped a lot (however, I don't use Beryl.)

I may be wrong (which is why I'm rechecking that thread now)
but I don't think you can get Beryl working with multiple monitor
support like this.

---

### Post by erimar77 on 2007-08-13
Here's another thread discussing the same problem:

[http://ubuntuforums.org/showthread.php?t=325929](http://ubuntuforums.org/showthread.php?t=325929)

---

