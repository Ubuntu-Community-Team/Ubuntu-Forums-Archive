---
title: "Remove mouse pointer?"
date: 2008-01-09
forum: Desktop Environments
---

### Post by Kumpe on 2008-01-09
I'm planning to use an old laptop of mine as a digital photoframe, or something like that. I have Ubuntu/Fluxbox installed, but i cant get rid of the mouse pointer. It always shows up in the center of the screen after startup, and i don't want to plug in a mouse everytime i boot up just to move it away.
Anyone got an idea how to disable it?

---

### Post by Anduu on 2008-01-15
Install Unclutter...it is in the repos
```
sudo apt-get install unclutter
```

Attached is a script I made....have the script run at startup and you should be good to go.

After 10 seconds the pointer should dissappear.

---

### Post by RedSquirrel on 2008-01-15
You can just add it to your ~/.fluxbox/startup.

```
unclutter -root -idle 12 &
```

is what I'm using, but you'll want to make your '-idle' option's value smaller.  (man unclutter)

---

