---
title: "Daemon/Atd Troubles"
date: 2009-04-04
forum: General Help
---

### Post by ShaunG on 2009-04-04
Apologies for re-threading asking same questions but I would really, REALLY like any help with the following.

I believe I am having problems with atd. 

These following threads are where I first asked for information:

[http://ubuntuforums.org/showthread.php?t=1115274](http://ubuntuforums.org/showthread.php?t=1115274)

[http://ubuntuforums.org/showthread.php?t=1115287](http://ubuntuforums.org/showthread.php?t=1115287)

I still cannot install tor.

However I am having some luck with the at command.

If I do

```
sudo touch /var/run/atd.pid
sudo atd&
```

I can get atd running. Then when atd is running if i run the at command from a seperate terminal it will not give me any errors, although it point blank refuses to work too.
However, the second I do anything from the first command line, (where atd& is) I get the atd process exit message. Which is infuriating.

Any help is really appreciated. I do not fully understand daemons, or atd or anything in /var/run and would just like to be able to get things working nicely. 
The at command is something I love and tor is something I'd really love to be able to get working.

Thank you for any and all help in advance,

~ Shaun

---

### Post by ShaunG on 2009-04-04
Anyone? :(

---

### Post by ShaunG on 2009-04-05
Bump, still looking for help. :confused:

---

### Post by ShaunG on 2009-04-06
Solved:

/dev/null and /dev/urandom and /dev/random had incorrect permission. Lord only knows how.

---

