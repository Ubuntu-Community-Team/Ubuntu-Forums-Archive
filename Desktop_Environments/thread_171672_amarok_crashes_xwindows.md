---
title: "amarok crashes xwindows"
date: 2006-05-07
forum: Desktop Environments
---

### Post by vavoem on 2006-05-07
When run as a normal user amarok crashes on startup and takes xwindows along with it in the process.

When run as sudo amarok no problem occurs.

I thought maybe it's a problem with the user configuration files of amarok.
so i threw away ~/.kde/share/apps/amarok with no result.

Is there a way to make a log of events that appear in terminal window so i can provide you with more information concerning this problem.
It gives some errors but it's just to fast to copy paste them,

---

### Post by Jussi Kukkonen on 2006-05-07
[QUOTE=vavoem]When run as a normal user amarok crashes on startup and takes xwindows along with it in the process.

When run as sudo amarok no problem occurs.
[/QUOTE]
Sounds really odd... Could the display driver be at fault, can you try with another one? 
> 
I thought maybe it's a problem with the user configuration files of amarok.
so i threw away ~/.kde/share/apps/amarok with no result.

Is there a way to make a log of events that appear in terminal window so i can provide you with more information concerning this problem.
It gives some errors but it's just to fast to copy paste them,

You can do 
```
amarok > logfile
```

---

### Post by vavoem on 2006-05-07
Thanks for your reply

The amarok > logfile.txt gave back nothing usefull however googling up the messages in the logfile provided me with the proper userconfiguration file wich is in
~/.kde/share/config and is called amarokrc 
I threw that one away and that seemed to do the trick.

Now playing :-({|=  music ;)

---

