---
title: "Problem switching my login screen theme with login window (it crashes)"
date: 2006-10-15
forum: Desktop Environments
---

### Post by gamingworld on 2006-10-15
Basically, when I try to open Login Window, it says "Starting admin app..." and then closes after a few seconds with nothing popping up. I've tried numerous fixes, nothing has worked for me. At the moment I'm missing my main GDM.conf file because of one of them. If i type gksu gdmsetup via terminal, this happens:

 Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 2 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 3 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 4 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 5 of 5.
  Command failed 5 times, aborting.
Could not access GDM configuration file.


If anyone could give me a hand that'd be great.

---

### Post by gamingworld on 2006-10-16
Bump..I'm just trying to reset the login screen to the original..:|

---

### Post by gamingworld on 2006-10-16
One more bump

---

### Post by gamingworld on 2006-10-16
Perhaps I worded this wrong? I was told on #ubuntu to ask here. Even a way to reset the login screen to the default ubuntu theme. Basically, I'm trying to get the selectable XGL session to be able to boot into KDE also, but also I'd like to be able to set my default session to XGL. Long story short I just want to reset my login screen.

---

### Post by kanna1620 on 2007-01-13
> **gamingworld said:**
> Basically, when I try to open Login Window, it says "Starting admin app..." and then closes after a few seconds with nothing popping up. I've tried numerous fixes, nothing has worked for me. At the moment I'm missing my main GDM.conf file because of one of them. If i type gksu gdmsetup via terminal, this happens:

 Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 2 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 3 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 4 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 5 of 5.
  Command failed 5 times, aborting.
Could not access GDM configuration file.


If anyone could give me a hand that'd be great.

Same problem with me!!! Plz somebody help me.

---

### Post by Stephen Howard on 2007-01-13
Maybe try:

apt-get --reinstall install gdm

---

