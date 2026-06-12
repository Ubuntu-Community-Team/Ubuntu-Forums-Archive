---
title: "Need help getting fvwm going"
date: 2007-03-11
forum: Desktop Environments
---

### Post by thypeacefrog on 2007-03-11
I'm using this guide.
[https://help.ubuntu.com/community/FVWM-Crystal#head-d3383460dd4d4ab0612da2d17d82de9b4d3297be](https://help.ubuntu.com/community/FVWM-Crystal#head-d3383460dd4d4ab0612da2d17d82de9b4d3297be)

and when it says to start the desktop using the *startx* command I get this message:


jack@jack-laptop:~$ sudo startx
xauth:  creating new authority file /home/jack/.serverauth.16000

X: warning; process set to priority -1 instead of requested priority 0

Fatal server error:
Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again.


xinit:  unexpected signal 2.



How can I fix it? =(

---

### Post by yabbadabbadont on 2007-03-11
You don't use sudo to run startx.  ;)

---

