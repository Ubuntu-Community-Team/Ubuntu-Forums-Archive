---
title: ".ICEauthority file is for?"
date: 2005-09-17
forum: Desktop Environments
---

### Post by shooterae5 on 2005-09-17
I've had an error a few times logging in using GDM, > Gnome or enlightenment.
I get an xsession message that tells me the .ICEauthority can't be read. 

to fix the problem I'll login to a text screen (Alt+Ctrl+F2) as my user and:
sudo rm .ICEauthority (@ the root level of my user)

then switch back to GDM (Alt+Ctrl+F7) and login as normal with out a problem.

Can someone tell me what the .ICEauthority file is for? It does reproduce itself after the next login.

Shooter

---

### Post by oneybm on 2005-09-17
I had that exact same problem for awhile when I first started with Ubuntu.  The explaination I got for the problem being caused was the use of the, KDE libs causing issues.  In my case it happened when I would use K3B to burn disks  I resolved it the same way you did and eventually doing an update fixed it. *shrug* No clue what changed.

As for what the file actually does, I never got an answer on that one.

Sorry I'm not of more help.

---

### Post by shooterae5 on 2005-09-17
thanks for the input. 

Although I'm not using the KDE desktop I am, from time to time, running Kdiskfree. 

It's likely to be one of the lib files that installed with Kdiskfree thats causing the my problem. 

Others (on other forums) have pointed in the same direction as to the cause of the problem but no one has yet been able to tell my what that file is for. 

Which isn't all that important, given I can fix it. 

I just like to understand why things work the way they do... I like the nuts and bolts.

your comments have have help me get a little closer to the info I'm looking for.  :)

---

### Post by cwaldbieser on 2005-09-17
[QUOTE=shooterae5]thanks for the input. 

Although I'm not using the KDE desktop I am, from time to time, running Kdiskfree. 

It's likely to be one of the lib files that installed with Kdiskfree thats causing the my problem. 

Others (on other forums) have pointed in the same direction as to the cause of the problem but no one has yet been able to tell my what that file is for. 

Which isn't all that important, given I can fix it. 

I just like to understand why things work the way they do... I like the nuts and bolts.

your comments have have help me get a little closer to the info I'm looking for.  :)[/QUOTE]

[http://www.linuxsa.org.au/mailing-list/2002-09/1318.html](http://www.linuxsa.org.au/mailing-list/2002-09/1318.html)
Doesn't go into great detail, but it explains it's basic purpose.

---

