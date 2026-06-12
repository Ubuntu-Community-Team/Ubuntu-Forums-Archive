---
title: "Free memory on Ubuntu"
date: 2008-12-12
forum: General Help
---

### Post by ramiyosef on 2008-12-12
hi all,

i have Ubuntu 8.10 installed on my laptop and its fully updated. the thing is the free memory is inconsistent between the command free-m and the GUI tool from System--> Administarion --> System Monitor.

e.g. free -m gives i have: used 1950, free: 64. while in GUI 487 MB used.

is this a bug or what?? anyone can advise plz. 

cheers

---

### Post by sdennie on 2008-12-12
You need to look at the second line of "free -m".  That should be more in line with the system monitor.  Some tools will consider the cache as free memory and some will consider it used memory (the former being what most people would expect).

---

### Post by ramiyosef on 2008-12-12
thx vor, the tool matches the cache free memory.

but i need to know what is the real value of the free memory? i dont think its the cache value, right? and what does the cache memory represent?

---

### Post by sdennie on 2008-12-12
In computers, caches are generally used to hide latencies and usually contain data that can be thrown away without doing harm to the system (other than making it slower by needing to get information that isn't in the cache).  The cache in this case hides disk latencies by holding things recently read from disk in memory so they don't need to be read from disk again.  As such, the first two lines of "free -m" are both correct.  Cached memory is technically being used but, it can be thrown away at any time to make room for memory that your applications need so, it can also be considered unused memory.  When most people think of "free" memory, they mean the amount of memory being used minus the cache (which is what you are seeing in gnome-system-monitor and the second line of free -m).

---

### Post by ramiyosef on 2008-12-12
its clear now, but why do you think the GUI tool use the used cache value? i think it is more logical to use the actual free memory!

---

