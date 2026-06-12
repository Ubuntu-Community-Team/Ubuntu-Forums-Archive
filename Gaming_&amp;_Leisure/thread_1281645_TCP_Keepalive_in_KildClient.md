---
title: "TCP Keepalive in KildClient?"
date: 2009-10-03
forum: Gaming &amp; Leisure
---

### Post by Grimhound on 2009-10-03
I'm throwing this out to coders and the like, though I know it's at best a longshot that anyone will see this topic with enough interest or knowledge to be able to assist. I just began using KildClient(a MUD client located in the Add/Remove Programs for Ubuntu) for running MU* environments, yet I have an issue. I am behind a router, and so it cuts off the connection without warning after a set period unless the connection pings back that it's still alive. This feature is commonly called a TCP KeepAlive with MU* clients, yet KildClient lacks this. I was curious if anyone had the knowledge and skill to investigate how and if it would be possible to integrate or add a KeepAlive to KildClient using the integrated options for scripts or plug-ins, or if anyone would know if there was anything already in existence to add in this feature. I would be greatly appreciative of any effort expended, as I know that many of you that frequent these forums are the best of the best in regard to this sort of thing regardless of modesty. :)

---

### Post by Vadi on 2009-10-04
I'd just make a periodic trigger for now. Didnt realize clients even had that feature

---

### Post by Grimhound on 2010-06-04
I am bumping this so-many-months later. I really want to see keepalive in KildClient. Not sure who I would talk to to see about that.

---

### Post by mgroat on 2010-09-19
Apparently, the newest version fixes that bug.  It doesn't seem to be in the repositories, but you can download the source to version 2.10.0 here [Here]("http://kildclient.sourceforge.net/phpwebsite/index.php?module=pagemaster&PAGE_user_op=view_page&PAGE_id=2").

**EDIT:**  Be sure to *sudo apt-get install libgtkspell-dev* if you want spell-checking to work.

---

