---
title: "[SOLVED] Evolution and evolution-data-server suck CPU and memory"
date: 2006-12-16
forum: Desktop Environments
---

### Post by pinkunicorn on 2006-12-16
Recently, my system often slows down to a crawl. I've noticed that the process list often looks something like this, without the system having run for extended periods of time:

```

 5397 hans      16   0 1022m 513m 4344 S  0.0 35.3   4:21.44 evolution-data-
31758 hans      16   0  737m 428m  13m S  0.0 29.4   2:19.57 evolution

```

Since I have 1.5GB of RAM, this is a rather significant memory usage.

Another, possibly related, problem is that Gaim usually takes a long time to start. I suspect that this may have something to do with the syncing of the Gaim buddy list and the Evolution address book.

The swelling of evolution and evolution-data-server can happen without me doing anything active with evolution (although, of course, it's receiving mails in the background now and then).

Help, please! ](*,)

---

### Post by dbbolton on 2007-01-01
my gnome-system-monitor lists these two entries:   ```
process name..........resident memory
evolution-data-server-1.6..........6.0MB
evolution-exchange storage..........9.1MB
```  i only have 1/2 gig of ram, so i typically scrape every bit i can out of this machine. from what you said above, these processes have to do with the contacts stored in Gaim. why can't i end them after gaim has started ?  


apparently, you have use br tags for breaks now.

---

### Post by MaX on 2007-10-01
I had this problem until this very second...

I had an exchange account configured but the password didn't match. When I removed the exchange account in Evolution the CPU levels went down instantly.

I guess it's the exchange plugin that is the hog.

---

### Post by pinkunicorn on 2007-11-15
"Solved" by retiring the machine and making a fresh install on a new one.

---

