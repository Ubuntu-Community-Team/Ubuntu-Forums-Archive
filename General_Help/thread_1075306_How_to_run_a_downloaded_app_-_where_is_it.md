---
title: "How to run a downloaded app - where is it ?"
date: 2009-02-20
forum: General Help
---

### Post by errolgreer on 2009-02-20
I used synaptic to install some software - (games) It said they were installed, but they do not appear under Applications. How do I find them and run them ? Excuse my ignorance re Linux.

---

### Post by heindsight on 2009-02-20
What games did you install? 

If they're games that are supposed to run in a terminal then they probably won't show up in the menu, you'd have to open a terminal and enter the command name for the game to play it.

If you know the names of the packages you installed you can use
```
dpkg -L package
``` to find a list of all the files that package installed (of course you have to replace package with the actual name of your package).

There's a very good chance that your games were installed under /usr/games

---

### Post by 3rdalbum on 2009-02-20
My signature has a video walkthrough of this common problem.

---

### Post by UbuntuNerd on 2009-02-20
"3rdalbum" I watched the video on your signature is pretty good!!!!

---

