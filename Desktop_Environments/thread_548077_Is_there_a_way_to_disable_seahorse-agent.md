---
title: "Is there a way to disable seahorse-agent?"
date: 2007-09-10
forum: Desktop Environments
---

### Post by dentament on 2007-09-10
Hi
I just use seahorse for key management
and don't need it to cache passphrases
but I can't find a way to disable it from loading on gnome start
it's not listed among the programs to start in "sessions"
and I can't find a key for this in gnome config tool
anyone can help?
thanks, bye

---

### Post by jernst on 2008-02-08
I wanted to disable it too on an old laptop and found the solution :

move or remove the corresponding files from /etc/X11/Xsession.d/ (for example 60seahorse)

---

### Post by dustigroove on 2008-06-03
It looks like this is a bit of an old thread, but for anyone that ends up here hopefully this may be of help...

> **dentament said:**
> ... I can't find a way to disable it from loading on gnome start it's not listed among the programs to start in "sessions" and I can't find a key for this in gnome config tool ...

A nice way to manage this and some various other runlevel symlinks is through a program in the repositories called "sysv-rc-conf".

```
sudo apt-get install sysv-rc-conf

```Once installed you can run sysv-rc-conf from a terminal and you should see entries for a variety of programs. Look for seahorse-agent and then just remove the X's for each runlevel.

Cheers,

---

