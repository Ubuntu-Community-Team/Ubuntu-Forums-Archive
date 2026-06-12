---
title: "Keyboard map messed up after update"
date: 2006-07-31
forum: Desktop Environments
---

### Post by sadiini on 2006-07-31
:confused:  After automatix upgrade I get a message:

Error activating XKB configuration.

It can happen under various circumstances:

-  a bug in libxklavier libary
-  a bug in X server (xkbcomp, xmodmap utilities)
-  X server with incompatible implementation

X server version 7.0, Dapper. 

I have not upgraded any Xorg packs. My locale is Estonian but I have no letters with dots, whitch I simply need for communication. 

Any clues, what to do next???
Reinstall X with all extras? 
Use some other driver? 
BTW, I noticed, that xorg.conf changed my locale to "ee". It used to be "et". I tried to change it, but it made no difference :(  

Out of clues :(

---

### Post by Ziox on 2006-07-31
try a sudo dpkg-reconfigure xserver-xorg, it might work, but i'm not 100% certain

---

### Post by sadiini on 2006-07-31
dpkg-reconfigure does not help at all :(
Same sad story as before...

---

### Post by arnieboy on 2006-07-31
none of the above errors are a direct result of using automatix or its repositories.
try doing the following:
```
xmodmap /usr/share/xmodmap/xmodmap.et
```

---

### Post by sadiini on 2006-08-01
xmodmap.ee did the trick

Thank You, Thank You :D

---

### Post by tjp.thomas on 2006-08-01
> **arnieboy said:**
> none of the above errors are a direct result of using automatix or its repositories.
try doing the following:
```
xmodmap /usr/share/xmodmap/xmodmap.et
```

What does it do??? I have the same problem...

---

### Post by sadiini on 2006-08-01
Well! It changed my keyboard map to locale "ee" back again. Unfortunatelly I must issue that command every time I switch my laptop on :(
Searching a way to make it permanent and default setting right now...

---

### Post by arnieboy on 2006-08-01
> **sadiini said:**
> Well! It changed my keyboard map to locale "ee" back again. Unfortunatelly I must issue that command every time I switch my laptop on :(
Searching a way to make it permanent and default setting right now...

add it to sessions --> startup

---

### Post by sadiini on 2006-08-01
> **arnieboy said:**
> add it to sessions --> startup

That idea crossed my mind as one possible solution. I don`t know, what caused that bug and I wondered, what will happen, when it gets fixed. Double xmodmap loading?
For now I will do exactly as You suggested. 
Thanks again!

---

