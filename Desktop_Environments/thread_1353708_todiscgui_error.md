---
title: "todiscgui error"
date: 2009-12-13
forum: Desktop Environments
---

### Post by Mia1990 on 2009-12-13
I finally got todiscgui to start working but i encode a avi and it keeps telling me that todiscgui had a error and can not continue here is the error i receive

> WARN: Skipping sector, waiting for first VOBU...
STAT: VOBU 0 at 0MB, 1 PGCS
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
todisc encountered an error:
There was a problem creating the DVD structure
Saving files in /tmp/todisc-work.0 so you can examine the situation
 
Does anyone know what is going on with this

---

### Post by Mia1990 on 2009-12-13
Has nobody seen this kind of error before

---

### Post by thatguruguy on 2009-12-13
I haven't been able to get it to work directly. Rather, I do the following:

1. I convert the file to a dvd-ready mpeg using WinFF (available in the repositories).
2. I run todiscgui from the terminal (because it's easier than remembering all the flags) and set all the options I want.
3. I hit the "Run todisc now" button after all options are set.
4. I close todiscgui, and go back to the terminal.  todiscgui generates a script which should still be visible in the terminal.  I cut it, paste it, and run it in the terminal.  Everything works as it should from that point forward.

---

