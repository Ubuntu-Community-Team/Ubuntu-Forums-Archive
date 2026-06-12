---
title: "[SOLVED] Liferea not starting in Xubuntu"
date: 2007-07-14
forum: Desktop Environments
---

### Post by psychobillyjekyll on 2007-07-14
Hi, 
I was wondering if anyone else has experienced liferea not loading in Xubuntu lately. Even if I start the process with the alt-F2 command, it won't load, it tries to start the process but then its immediately killed by something.

Thanks
Justin

---

### Post by bapoumba on 2007-07-15
Any error if you run ```
liferea
``` from a terminal?

---

### Post by psychobillyjekyll on 2007-07-15
The error code was :
> ** (liferea:15023): WARNING **: XML error while reading cache file! Could not import "/home/username/.liferea_1.2/feedlist.opml"!
** ERROR **: Fatal: Feed list import failed! You might want to try to restore
the feed list file /home/username/.liferea_1.2/feedlist.opml from the backup in /home/username/.liferea_1.2/feedlist.opml.backup
aborting...
Aborted (core dumped)


I just restored it and it worked.

thanks
Justin

---

### Post by bapoumba on 2007-07-16
Glad to see you sorted this out.
BTW, I marked your thread as solved (you have an option for it in the "thread tools" menu).

---

