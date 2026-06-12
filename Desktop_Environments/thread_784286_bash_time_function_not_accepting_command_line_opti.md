---
title: "bash time function not accepting command line options"
date: 2008-05-06
forum: Desktop Environments
---

### Post by pwaltman_1972 on 2008-05-06
Don't think this is just limited to Ubuntu... or maybe I just don't get it, but the Ubuntu man page states that:

[INDENT]Options to time must appear on the command line before COMMAND.  Anything on the command line after COMMAND is passed as arguments to COMMAND[/INDENT]

and gives the example:

[INDENT]time -f "%E real,%U user,%S sys" ls -Fs[/INDENT]

however, when you try that bash reports that it can't find the program "-f", i.e.:

[INDENT]bash: -f: command not found[/INDENT]

heck, not even time --help works.

I tried this on a Redhat box and it doesn't work there either, so I suspect that this is a general problem... or the man pages is way out of date

Is anyone else seeing this?  Where/who would I report this to?

---

### Post by VaebnKehn on 2008-12-24
I'm having the same issue here.  Any information would be greatly appreciated.

---

### Post by VaebnKehn on 2008-12-24
Appearently bash has its own version of time.  To run the time program you have to call it explicately: "/usr/bin/time"  see: [https://bugs.launchpad.net/gnubash/+bug/238061](https://bugs.launchpad.net/gnubash/+bug/238061)

---

