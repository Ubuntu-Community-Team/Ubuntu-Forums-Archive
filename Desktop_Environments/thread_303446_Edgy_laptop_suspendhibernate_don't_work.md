---
title: "Edgy laptop suspend/hibernate don't work"
date: 2006-11-20
forum: Desktop Environments
---

### Post by NiksaVel on 2006-11-20
Hey all,

I have finally finished up configuring everything on my laptop with ubuntu edgy, only one thing remains to be done properly...

Suspend and hibernate don't work as they should...

Suspend actually does suspend the computer, but when I turn it back on it either get's it up properly, but my networking is gone and have to reboot or it gets me to a frozen blank screen...


Hibernate howere does not work at all, it just starts shutting down things and either returns me to the login screen or hangs on a blank screen.



I have made a suspend script using this howto: [http://www.linux.com/article.pl?sid=06/05/24/1716222](http://www.linux.com/article.pl?sid=06/05/24/1716222) and it works 100% so far.  However, I would like to know:
How to have this script execute when I press the Shut down/Suspend button, if possible, and if now how to make it like an icon on the desktop that I can just double click and suspend (the prob is that I have to run it from a terminal with a sudo command)...


I have not tried the hibernate howto on the same page cuz it looks a bit complicated so far...  




any help will be muchly appreciated!


cya
NiksaVel

---

### Post by earobinson on 2006-11-20
try the how to would be my guess, and if it still dont work report it as a bug, worked out of the box for me :)

---

### Post by NiksaVel on 2006-11-20
heh... it's not exactly written for ubuntu ...  and my general linux knowledge is limited so it's a prob...

but even if I manage to make a script that would work I would still like to know how to map that script to the suspend or hibernate buttons... :)


is there perhaps an ubuntu howto covering this topic?

---

### Post by NiksaVel on 2006-11-21
bump :-D 


I still need some help

---

### Post by mikedeatworld on 2006-11-21
you could run dhclient to help with the networking issue. just a thought...

---

