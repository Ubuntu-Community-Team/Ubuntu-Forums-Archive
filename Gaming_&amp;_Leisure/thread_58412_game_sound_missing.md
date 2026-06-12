---
title: "game sound missing"
date: 2005-08-20
forum: Gaming &amp; Leisure
---

### Post by kamiccolo on 2005-08-20
Perhaps this problem is already known:
I installed such pretty games like tuxracer and supertux via synaptic, but there's no sound. The graphic is perfect, but how can I get the sound?

---

### Post by gerbman on 2005-08-20
[QUOTE=kamiccolo]Perhaps this problem is already known:
I installed such pretty games like tuxracer and supertux via synaptic, but there's no sound. The graphic is perfect, but how can I get the sound?[/QUOTE]

Try disabling Ubuntu's sound server (it's probably conflicting with the game's sound).  Go to "System", "Preferences", "Sound Preferences", and uncheck "Enable sound server startup".

It's kind of a pain to have to do it any time you play a game, but I'm not sure of a better solution.

---

### Post by kamiccolo on 2005-08-20
This works, but how can I configure Ubuntu that I don't have to shutdown and startup the soundserver any time I want to play?

---

### Post by ed101 on 2006-10-06
FYI I installed Postal Classic from Loki with root, I had to make a script with "killall esd ; postal" in /usr/bin/ to start it and for the sound to work. 

You can test to see if it works by typing in "killall esd" then start the game from terminal.

Im running Ubuntu 6.06.1

Adam:KS

---

