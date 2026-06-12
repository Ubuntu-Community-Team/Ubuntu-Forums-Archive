---
title: "RSS-grab in Gdesklets problem"
date: 2006-05-31
forum: Desktop Environments
---

### Post by chokes on 2006-05-31
hi all i installed gdesklets an gdesklets-data so... when i want to load rss-grab i got this error:
Could not find sensor 'rssgrab'
/usr/share/gdesklets/Displays/rss-grab/rssgrab.display



A sensor could not be found. This usually means that it has not been installed.

so i go to this directory an all the file is here....](*,) 
so i dont know what to do next.....

---

### Post by KrIaXPaTaLa on 2006-06-04
I have the same problem. I've search for a rssgrab package with apt-get, but got none. 

Regards,

KrIaX, Portugal

---

### Post by Salluste on 2006-10-07
> **KrIaXPaTaLa said:**
> I have the same problem. I've search for a rssgrab package with apt-get, but got none. 

Regards,

KrIaX, Portugal

Same problem and still no response here... So I try several things...

I have installed python-feeparser package :

[SIZE="2"]Universal Feed Parser for Python
Python module for downloading and parsing syndicated feeds. It can
handle RSS 0.90, Netscape RSS 0.91, Userland RSS 0.91, RSS 0.92, RSS
0.93, RSS 0.94, RSS 1.0, RSS 2.0, Atom, and CDF feeds.
It provides the same API to all formats, and sanitizes URIs and HTML.[/SIZE]

and now it works !

Maybe very late for the response but could be usefull to other late installers using google.

Nicolas .

---

### Post by junkalam on 2006-11-29
Yup it works now...

Thanks Salluste !!!

---

### Post by MurDoK on 2008-02-05
Hi all.
One year later the bug is still there.
someone should add python-feedparser as dependence or at least change the rss plugin to show a bit more explanatory error message.

---

