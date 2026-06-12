---
title: "Evolution-exchange calendar lost sync"
date: 2008-09-08
forum: Desktop Environments
---

### Post by prostar on 2008-09-08
This is just a note for people who messed up their calendar like me.  Only some meetings were showing up, some recurring meetings had only one instance, etc...  I was looking for a way to re-sync with exchange.  Everything looked fine in outlook web access, but I couldn't get it to download into evolution.  Eventually I found the cache file in:

~/.evolution/exchange/(account@work.com)/folders/calendar/cache.ics

I deleted this file, and on the next run it got all the right information.

Now if I could do the same for my inbox...

**UPDATE:**
Without finding an official solution, here's how I forced it to download the older messages...

Exit Evolution:
```
evolution --force-shutdown
```
Backup your $HOME/.evolution:
```
tar -cvfz ~/myevo.tgz ~/.evolution
```
Clean out the crap:
```
rm  -rf  .evolution/exchange/ .evolution/mail/exchange/
```
Restart evolution ( it may take a few minutes to re-sync ).

* Credit to evolution mailing list "Reid Thompson"

---

### Post by linux.girl on 2011-12-09
I am looking for a way to sync evolution calendar with exchange - you seem to have experience with that, do you think you could point me in the right direction?

---

