---
title: "intalling quake4 on ubuntu hardy x64"
date: 2008-05-21
forum: Gaming &amp; Leisure
---

### Post by Barasuishou on 2008-05-21
how do i install it and make it work, y have read some "step by step" articles about it but i can't get it to work, can someone help me please??, i'll be waiting for answers, bye.

---

### Post by Barasuishou on 2008-05-22
hey well i got the .run file(installer) to run well, but at the middle of the installation it tells me i don't have permission to write the directory where i am trying to install it, so does someone know how can i give the permission to write it??,

---

### Post by Sleaka J on 2008-05-22
I imagine that the directory it's trying to install to is /usr/local/games/quake4

Go to a terminal and type the following:

sudo chown <insert your username here> /usr/local/games

In my case I'd type:

sudo chown sleakaj /usr/local/games (as sleakaj is my username).

---

### Post by Cappy on 2008-05-22
You would have to use sudo chown.

The normal thing to do is to run the installer with sudo or install the game in your home directory.

---

### Post by Sleaka J on 2008-05-22
> **Cappy said:**
> You would have to use sudo chown.

The normal thing to do is to run the installer with sudo or install the game in your home directory.

The only problem I see with running the installer with sudo is that some installers run the game after you install it and that creates a config directory in your home folder (/home/<username>/.quake4/ in this case) with root privileges only, in which case you'd have to chown it anyway.

If the installer drops you back to the terminal after installing, then you won't have that problem. However, I know that I had this problem after installing ioquake3 using sudo.

---

### Post by Brebs on 2008-05-22
Just run my (reasonably) [foolproof script](http://www.fedoraforum.org/forum/showthread.php?t=189064) ;)

---

### Post by Perfect Storm on 2008-05-22
The only reason to install a game in the system is if you run multiply accounts/logins on your computer which will use the same game when they are logged on. Else install it it in your home directory, it's safer to do so. Not recommendable you start trying messing with the systems permission options.

---

