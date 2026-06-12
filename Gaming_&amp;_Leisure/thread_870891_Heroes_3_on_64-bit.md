---
title: "Heroes 3 on 64-bit"
date: 2008-07-26
forum: Gaming &amp; Leisure
---

### Post by alican timur on 2008-07-26
i'm trying to run Heroes 3 on my 64-bit hardy heron, and i got the 64bit error, got through with it by

```
sudo linux32 bash ./setup.sh
```

now i'm getting:

```
alican@Alican-HQ:/media/cdrom0$ sudo heroes3
X Error:  158
  Request Major code 137 (XFree86-DGA)
  Request Minor code 1 ()
  Error Serial #17
  Current Serial #17

```

when i try to run the game. help please?

---

### Post by alican timur on 2008-07-27
bump

---

### Post by vlax on 2012-09-17
Copy all the contents form the cd somewhere in your home folder.

Right click on setup.sh and change it to be executable.

Open terminal in that directory and type:

```
sudo linux32 bash setup.sh
```Say "y" to every question (to install all game data) exept after instal when the game ask to start as root.

Close the terminal and reopen it. Type heroes3 to start the game. The game will start but there is the problem with the sound. In 1999. Pulse audio doesn't exist. I don't know how to fix the audio problem. :-({|=

---

