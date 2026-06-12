---
title: "How can I revert back, when I think I corrupted an install?"
date: 2006-07-17
forum: Desktop Environments
---

### Post by JesusXP on 2006-07-17
Hi guys,

I was trying to install Enlightenment E17 for Dapper Drake, and everything has gone horribly awry :-k  I feel like I've been banging my head at a wall, because I have searched vigourously for an easy way out, and it didnt look like it was happening (easy installation). I finally ended up downloading the files from enlightenment.freedesktop.com or similar, and individually compiled the neccessary peices with ./configure; make; make install; however when I tried to change my session I have no "enlightenment" session, but a "foo" session, and enlightenment will crash upon trying to swith to said "foo" session. Now I apalogize for the weak description of my problem, but I feel like its worth giving up at this point, if there is such a way for me to uninstall what it was I compiled. I'm just posing the question now as I leave work.

Many thanks in advance.

---

### Post by az on 2006-07-17
> **JesusXP said:**
> Hi guys,

I was trying to install Enlightenment E17 for Dapper Drake, and everything has gone horribly awry :-k  I feel like I've been banging my head at a wall, because I have searched vigourously for an easy way out, and it didnt look like it was happening (easy installation). I finally ended up downloading the files from enlightenment.freedesktop.com or similar, and individually compiled the neccessary peices with ./configure; make; make install; however when I tried to change my session I have no "enlightenment" session, but a "foo" session, and enlightenment will crash upon trying to swith to said "foo" session. Now I apalogize for the weak description of my problem, but I feel like its worth giving up at this point, if there is such a way for me to uninstall what it was I compiled. I'm just posing the question now as I leave work.

Many thanks in advance.


Can you log into any other session?

If you still have the source bits you should be able to make uninstall....

---

### Post by JesusXP on 2006-07-17
turns out it was an improperly produced file, I just needed to edit up e17.desktop in /usr/share/xsessions 

I ended up figuring it out on the train on my way home from work, and MAN was I happy! lol.. I personally had little luck searching around for installation tips, running e17 on Dapper Drake, all the resources were old and from Breezy / Warty, and no longer applicable really. I'd be happy to write out a short and sweet lil tutorial on what I did. 

Thanks for responding :)

---

