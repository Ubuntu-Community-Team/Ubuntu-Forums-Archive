---
title: "Run adesklets on startup"
date: 2006-09-03
forum: Desktop Environments
---

### Post by FrederikVds on 2006-09-03
I want to start adesklets when gnome starts.

I tried going to System > Preferences > Sessions and adding /usr/bin/adesklets --nautilus to the startup programs list, but it doesn't work.
When I type /usr/bin/adesklets --nautilus in a terminal it does work.
How should I fix this?

Thanks

---

### Post by BitTorrentBuddha on 2006-09-03
It might need to wait for some things to load before it, I would try having it wait 15 seconds before running:```
sleep 15 && /usr/bin/adesklets --nautilus
``` In place of "/usr/bin/adesklets --nautilus" in the start-up scripts. Post back if that doesn't work or if waiting 15 seconds doesn't appeal to you.

---

### Post by FrederikVds on 2006-09-03
Doesn't work :(
But I'm adding it using the GUI tool, could it be that I have to add it to a script manually instead?

---

### Post by shane2peru on 2006-11-13
Has anyone ever figured this out?  I would like to know this too.  Thanks!

Shane

---

### Post by shane2peru on 2006-11-23
Hey, I got it!!! ```
adesklets -d 25 --nautilus
```  put this in the startup thing under sessions.  This is for Gnome.  Probably you would replace nautilus with kde for you KDE users.  the 25 is seconds, it is a delay.  Enjoy!!

Shane

---

### Post by FrederikVds on 2006-11-23
> **shane2peru said:**
> Hey, I got it!!! ```
adesklets -d 25 --nautilus
```  put this in the startup thing under sessions.  This is for Gnome.  Probably you would replace nautilus with kde for you KDE users.  the 25 is seconds, it is a delay.  Enjoy!!

Shane

Thanks a lot!

---

