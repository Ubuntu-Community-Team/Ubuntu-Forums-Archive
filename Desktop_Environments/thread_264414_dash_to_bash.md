---
title: "dash to bash"
date: 2006-09-24
forum: Desktop Environments
---

### Post by IusedTObeSOMEONEelse on 2006-09-24
Hi every one! After upgrading 3 times I fianally succeeded. Now my Frostwire didn't make the transition as I need to change "dash" to "bash". Can any one please assist me, in plain simple terms as I don't want to 'ruin' a good thing?  Thanks so much.

---

### Post by ayoli on 2006-09-24
the first way (easy, one step):
```
sudo ln -sf /bin/bash /bin/sh
```

or (better) find the script which launch frostwire:
```
which frostwire
```
should give you a result like this: /usr/bin/frostwire
then:
```
gksudo gedit /usr/bin/frostwire
```
at the beginning of file, you ll find a line:
```
#!/bin/sh
```
replace **sh** with **bash** in this line

---

### Post by DougieFresh4U on 2006-09-24
Thanks so much!! Frostwire is now working. Now I don't understand what is going on with my gaim? I dont' get the sign on screen but all worked with dapper

---

### Post by IusedTObeSOMEONEelse on 2006-09-24
Thanks. Up & running frostwire.

---

