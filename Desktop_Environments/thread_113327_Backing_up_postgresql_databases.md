---
title: "Backing up postgresql databases?"
date: 2006-01-06
forum: Desktop Environments
---

### Post by derrick1985 on 2006-01-06
Hey,

I recently made a server (it's running debian etch, ubuntu wouldn't load on it) it's all text based. Anyways, on my ubuntu machine, i have a few databases iw ould like to back up and import into the new server, how could i do that (it would all be text bases as there is no gui on the new server)

Thanks.

---

### Post by soops1966 on 2006-01-06
You can DUMP the database on your Ubuntu machine, then import it into the Etch machine. 

It's well documented in the Postgres docs.

---

### Post by browneyedgirl65 on 2006-02-02
I'm curious about that.  What about tarballing or copying or whatever the /var/lib/postgresql/8.0/main directory?

Dump definitely has its uses, but would the above approach be easier/better/worse/simple alternative/whatever to dumping?

(Erm, please note I'm addressing a more general issue of backing up db's as opposed to relocating them...my eye was caught by the subject line more than the text...)

---

