---
title: "Can't start Quake3 unless I use sudo"
date: 2008-01-14
forum: Gaming &amp; Leisure
---

### Post by ChEeZeBaLL on 2008-01-14
Hello people i'm new to Ubuntu and last night I installed Quake 3. The game runs fine and all, but the startup icons placed in the Gnome menu dont work and in order to start the game from a terminal I have to type "sudo quake3". I think I installed the game with the wrong file permissions set or something.

How can I fix this?

---

### Post by ChEeZeBaLL on 2008-01-14
anyone?

---

### Post by Mb0742 on 2008-01-14
reinstall or try sudo chmod 775.

---

### Post by ChEeZeBaLL on 2008-01-15
thanks sudo chmod 775 /usr/local/games/quake3
and
 sudo chmod 775 /usr/local/games/quake3/baseq3 fixed the problem.

Now I just need to get internet play to work.

---

