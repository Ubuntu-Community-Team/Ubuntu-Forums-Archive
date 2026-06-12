---
title: "Gnome-terminal crashes on opening second window"
date: 2006-09-14
forum: Desktop Environments
---

### Post by wzzrd on 2006-09-14
When I have an instance of gnome-terminal open (no matter how many tabs) and I open a second gnome-terminal instance in a new windows, very often both instances crash. It is driving me mad. I saw there were some posts about this about this time last year, but I couldn't find a proper sollution. I'm running 6.06 with some repos (like beerorkid) on an XGL box. Everything else runs fine, the only crashes that do occur are the gnome-terminal ones.

I tried getting some crash info, but Murphy's Law stops me from having gnome-terminal crash when I want it to. Will post info when I have more 'luck'. 

I did notice a lot of this stuff on my xterm from which I ran gnome-terminal:

```

** (gnome-terminal:28058): WARNING **: can not run /usr/lib/libvte4/gnome-pty-helper
```

Please help. Bashing head against desk is starting to hurt.

---

### Post by mwolfe on 2006-10-23
hey i have the same problem.. I could never figure out how to duplicate the problem until i did some research and found someone else with the same problem figure out when it did it. If you open two instances of gnome terminal, then close one, then open another one it will crash..
there are other cases when it will crash as well but i have not figured it out exactly.
I am running xgl+beryl and i had the same problem with compiz and in regular gnome i believe.
However if i login to kde which is installed on my system as well, gnome-terminal doesnt crash.

The user with the same problem that i found online had a solution of removing all the non stable sources in your apt sources.list and then downgrading packages 
eventually he got his gnome terminal working fine.. I dont wanna go through all that though, it would be nice if i could figure out whats making it crash but i'm not sure how.

Anyone got any ideas?

---

