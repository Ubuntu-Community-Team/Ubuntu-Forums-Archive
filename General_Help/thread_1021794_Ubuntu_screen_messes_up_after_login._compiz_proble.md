---
title: "Ubuntu screen messes up after login. compiz problem"
date: 2008-12-25
forum: General Help
---

### Post by Gondee on 2008-12-25
The computer is a Dell mini 9. With Ubuntu 8.10 installed. When i was messing with the compiz settings. I clicked desktop switcher on, and it said in order to do so, it had to disable color negative switcher. I said yes, then the screen flashed, and there was purple lines everywhere. Not i  can not log in, if i try it does that then goes back to the log in. However i can log in in Failsafe terminal. But me not being a terminal man, i don't exactly know how to do anything. 

I'm thinking if i can re instate to original window manager, then fix the compiz setting i can gat it back?

Thanks for the help all. =)  Merry Christmas to!:)

---

### Post by gettinoriginal on 2008-12-25
Put this in terminal and it will restore compiz defaults:  :P

gconftool-2 --recursive-unset -a /apps/compiz

---

### Post by Gondee on 2008-12-25
=) that worked great!!!

thanks for the help, and once again Merry Christmas :)

It must have been just something i messed up....

---

### Post by gettinoriginal on 2008-12-25
That's the nice thing about linux, mess it up, fix it, crash it, reinstall it.  LOL

And Merry Christmas to you also:

Please go to tools and mark this as solved :P

---

