---
title: "Insecure directory in $ENV{PATH} while running with -T switch at /usr/bin/pg_ctlclust"
date: 2008-08-07
forum: Desktop Environments
---

### Post by pablogayar on 2008-08-07
Hi! I'm new here.
I've looking for a solution to a problem with postgresql i described in the title of this post.
But i got to solve this problem after some hours and its very simple.
i couldn't post a reply in the old thread, so i write the very simple solution here expecting it may help somebody.
it's a simple problem of permissions in /bin, so if you change the permissions to rwx rw rw it's runs ok. (chmod 755 /bin)
Hope it could help somebody and sorry for my horrible english.

---

### Post by amrish_2809 on 2009-01-19
Hi Friend,

Thanks for giving me the exact solution. 

I am new bee to Linux and i also face the same problem, which gets solved by your solution.

Thanks once again.:guitar:

Amrish the Jaiswal

---

### Post by filipei on 2009-09-16
Yes! Its working!
Congrats and thanks...

This is a simple and exact solution for this problem! There are a lot of other hard solutions!

---

