---
title: "gaim crashes after MSN connects"
date: 2006-07-05
forum: Desktop Environments
---

### Post by kaje on 2006-07-05
I recently installed gaim, and I can connect to my Y! and AOL IM accounts, but as soon as MSN connects, gaim crashes. No errors or anything. The program just disappears. I can see that it connects because the program crashes about a second after I see my MSN contacts appear online. Anyone know what's causing this?

---

### Post by dngpng on 2006-07-07
I also have this problem. Sometimes it could last a little longer time until you start to send or receive messages.

I tried to start gaim from command line, when it crashes, there is some error message as follow:

```
Gaim has segfaulted and attempted to dump a core file.
This is a bug in the software and has happened through
no fault of your own.

It is possible that this bug is already fixed in CVS.
If you can reproduce the crash, please notify the gaim
maintainers by reporting a bug at
http://gaim.sourceforge.net/bug.php

Please make sure to specify what you were doing at the time,
and post the backtrace from the core file. If you do not know
how to get the backtrace, please get instructions at
http://gaim.sourceforge.net/gdb.php. If you need further
assistance, please IM either SeanEgn or LSchiere and
they can help you.
Aborted
```

Dont know what that means, hope there is a solution ...

---

### Post by kaje on 2006-07-07
> **dngpng said:**
> I also have this problem. Sometimes it could last a little longer time until you start to send or receive messages.

I tried to start gaim from command line, when it crashes, there is some error message as follow:

```
Gaim has segfaulted and attempted to dump a core file.
This is a bug in the software and has happened through
no fault of your own.

It is possible that this bug is already fixed in CVS.
If you can reproduce the crash, please notify the gaim
maintainers by reporting a bug at
http://gaim.sourceforge.net/bug.php

Please make sure to specify what you were doing at the time,
and post the backtrace from the core file. If you do not know
how to get the backtrace, please get instructions at
http://gaim.sourceforge.net/gdb.php. If you need further
assistance, please IM either SeanEgn or LSchiere and
they can help you.
Aborted
```

Dont know what that means, hope there is a solution ...


I reinstalled gaim from automatix and it appears to be working now. Give that a try.

---

### Post by dngpng on 2006-07-07
> **kaje said:**
> I reinstalled gaim from automatix and it appears to be working now. Give that a try.

Unfortunately Gaim 2.0 beta doesnt work here. I need to use "use HTTP connection" because some ports are blocked at the gateway. But this version may have some problem using HTTP connection to login.

So, still couldnt understand what happens to my gaim 1.5.

Well, thanks all the same. ;)

---

### Post by dngpng on 2006-07-10
I think I maybe find the reason.

I tried to run gaim several times (with crashes, certainly :b) using ```
gaim --debug > gaim.log
``` and realized that it wrote the same thing at the end of each log:

```
msn: Processing queue
msn: Sending message
msn: C: SB 001: MSG 3 D 831
msn: S: SB 001: MSG encarta@conversagent.com Encarta®%20Instant%20Answers 557
g_log: gaim_base64_decode: assertion `text != NULL' failed
```

So i guess it is to some extent due to the Encarta robot in my contact list. I just delete it (in a few seconds before it crashes, maybe it's easier to use MSN messenger to delete it under Windows ;) ). Then, no crashes anymore! :)

Do you have Encarta robot in you list, kaje? Maybe you could also do this to figure out the problem with your gaim1.5.

---

### Post by kaje on 2006-07-10
> **dngpng said:**
> I think I maybe find the reason.

I tried to run gaim several times (with crashes, certainly :b) using ```
gaim --debug > gaim.log
``` and realized that it wrote the same thing at the end of each log:

```
msn: Processing queue
msn: Sending message
msn: C: SB 001: MSG 3 D 831
msn: S: SB 001: MSG encarta@conversagent.com Encarta®%20Instant%20Answers 557
g_log: gaim_base64_decode: assertion `text != NULL' failed
```

So i guess it is to some extent due to the Encarta robot in my contact list. I just delete it (in a few seconds before it crashes, maybe it's easier to use MSN messenger to delete it under Windows ;) ). Then, no crashes anymore! :)

Do you have Encarta robot in you list, kaje? Maybe you could also do this to figure out the problem with your gaim1.5.

Yeah, I do. It appears to work for me now though. Even with him there. But great find!

---

### Post by dngpng on 2006-07-10
> **kaje said:**
> Yeah, I do. It appears to work for me now though. Even with him there. But great find!

I just did a search at sourceforge, and confirm this by a bug report: [http://sourceforge.net/tracker/index.php?func=detail&aid=1519591&group_id=235&atid=100235](http://sourceforge.net/tracker/index.php?func=detail&aid=1519591&group_id=235&atid=100235)

---

### Post by kaje on 2006-07-10
I have yet to try and talk to him, so I may still get the crash. I'll try later.

---

