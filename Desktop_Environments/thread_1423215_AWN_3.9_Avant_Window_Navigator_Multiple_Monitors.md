---
title: "AWN 3.9 Avant Window Navigator Multiple Monitors"
date: 2010-03-06
forum: Desktop Environments
---

### Post by dccrens on 2010-03-06
Posting this in a new thread. 

Anyone know how to get AWN to run on two monitors? I want a bar on each monitor. 

I used to be able to start two instances using a shell script below but that doesn't seem to be working now. 

```
#!/bin/bash


killall avant-window-navigator
sleep 4

DISPLAY=:0.0 avant-window-navigator &
sleep 4

DISPLAY=:0.1 avant-window-navigator &
```

Playing around more with this and it looks like avant no checks to see if there is another instance running and will not start if there is. That is a bummer. Any way to change this?

dccrens@cavermax-ubuntu:~$ DISPLAY=:0.0 avant-window-navigator &
[1] 15569
dccrens@cavermax-ubuntu:~$
** (avant-window-navigator:15569): WARNING **: Another instance of Awn is running


[1]+ Done DISPLAY=:0.0 avant-window-navigator

---

### Post by zip_000 on 2010-05-03
I realize this is over a month old now, but I'm having the same issue and was wondering if you, or anyone else, has come up with a solution.

I have two monitors using separate x screens, and I would like a dock on each monitor.

Using separate x screens means that I can't drag and drop windows from one screen to the other, so I really need a dock on each monitor...or I could just leave the panels on the second monitor, but I would rather use the dock.

Thanks!

---

### Post by Kirky_D on 2010-05-25
Bump. Would also like to know if awn can have multiple instances on two monitors

---

### Post by fabounet on 2010-05-26
Not AWN but with GLX-Dock you can have several main docks without needing to launch it several times (which would be a waste).

---

