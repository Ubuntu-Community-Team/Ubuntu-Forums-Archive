---
title: "bash conditionals on the command line, launching only one copy of a process"
date: 2006-07-12
forum: Desktop Environments
---

### Post by soulcoughy on 2006-07-12
So, what i'm trying to do is only allow one instance of a particular executable, something like this:

if [ ps -C grip -o pid --no-headers > 0 ]
then
   grip
fi

Now, I can do this is a bash script no problem (i think), but is there a way to just enter this straight into a bash prompt in one fell swoop?  I.E.:

if { ps -C grip -o pid --no-headers > 0 } { grip }
or
if [ ps -C grip -o pid --no-headers > 0 ] ; then grip fi

(neither of those work by the way)

I guess there's no real reason I HAVE to do things this way, but I'm curious what I was doing wrong, as I see no reason it shouldn't work.  There is probably already a unix utility that checks for a running version of a process before launching that I don't know about too.
Thanks. 
-Brian

---

### Post by sciyoshi on 2006-07-12
You can do it on one line like this:

if [ -n `ps -C program -o pid --no-headers` ]; then program; fi

The reason I think your's wasn't working was because of the ' > 0 ' part. To do numeric comparison you need to use -gt, -lt, -eq, etc.
Samuel

---

