---
title: "two for two tonight"
date: 2006-12-27
forum: Gaming &amp; Leisure
---

### Post by loserboy on 2006-12-27
ugh... my second game tonight not working - Creatures 3

I think I need to uninstall and start all over can someone tell me how to do that

creatures 3 Internet edition

---

### Post by Perfect Storm on 2006-12-28
Go to the creatures folder and run the uninstaller script.

Eg.
sudo sh /usr/local/games/creatures3/uninstall

---

### Post by loserboy on 2006-12-28
thanks for that but i still cant get the thing to work, i followed what you said to someone about changing the $11 to $10 but still nothing, in fact the only thing showing up in my games list is the docking station, but  that wont run either...  any ideas?

---

### Post by Perfect Storm on 2006-12-28
Try follow it again and post the in/output

---

### Post by loserboy on 2006-12-28
I'm at work now, but last night i noticed when i check the creatures3 file again to make sure it was changed and still showed $11 instead of $10, but i couldnt gedit it even with sudo, it said something about time stamp too far in future or something..... when i get home ill post the actaul message if thats not enough for u

---

### Post by loserboy on 2006-12-29
ok I uninstalled creatures then followed the steps, tried to run

> 
dockingstation nocheck

then it said

> Creatures 3 found at /usr/local/games/creatures3
Pointing to directories
Creatures 3 is installed, connecting to it
Querying language
/usr/local/games/dockingstation/langpick: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory


also creatures is still not showing up on my game list.
is there a way to uninstall the docking station maybe i should do that too.

in the mean time im gonna go install libgtk-1.2.so.0 i guess

---

### Post by Perfect Storm on 2006-12-30
Aye. 

```
sudo aptitude install libgtk1.2
```

Going to add that to the howto.


Going to docking station folder and run the uninstaller script.

---

### Post by loserboy on 2006-12-30
there is no uninstall in the dockingstation folder

er wait does the install also work as the uninstall?

---

### Post by loserboy on 2006-12-30
ok cool i can run the docking station now.... is there a way i can just run creatures 3?


also i appreciate all the help i woulda never gotten that

---

### Post by blueamcat on 2008-01-30
Hmm, I've been without Docking Station/Creatures 3 for some time now. Ever since I got my 64 bit system. Wonder if it'll work...I'm running Gutsy. No harm trying right? I really loved that game. I've been a Creatures fan since I was 12! ...10 yrs ago. wow.

---

### Post by blueamcat on 2008-07-23
yea so I forgot to post my findings. it didn't work. ah well, maybe sometime in the future. ;)

---

