---
title: "GNOME does not load until esd is killed"
date: 2006-11-11
forum: Desktop Environments
---

### Post by absnewby on 2006-11-11
My first two installs of edgy and dapper did not go well. On login, I was faced with a brown screen and nothing else. After some searching I found that this solution works

[http://www.ubuntuforums.org/showthread.php?t=102359&highlight=brown+screen+login]("http://www.ubuntuforums.org/showthread.php?t=102359&highlight=brown+screen+login")

Now everytime I login, I have to switch to command line using Ctrl + Alt +F1
and use 

sudo killall -9 esd

after this I can login GNOME loads completely. Why is this? Is there a way to fix this issue?

---

### Post by key134 on 2006-12-08
I am bumping this because I have the same problem.  I replaced my soundcard (turned off the onboard and installed an SB Audigy) just like senectus in the other thread.  Any fix yet?

Keith

---

