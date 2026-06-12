---
title: "Cannot load tge Xfce desktop"
date: 2009-12-06
forum: Desktop Environments
---

### Post by Rocafort8 on 2009-12-06
When I login an user and the desktop is loading, the screen flashes and the login screen appears again.
 
I tried to login with Xterm but it also doesn't work.
 
Some time ago, I had a similar problem, but then I could login with Xterm and init the desktop with xfce-panel ( or something like that ) and "magicaly" the problem was solved one day ( not sure if it is something related with this ).
 
I don't know what logs should I post to report this bug .

---

### Post by ibuclaw on 2009-12-06
> **Rocafort8 said:**
> When I login an user and the desktop is loading, the screen flashes and the login screen appears again.
 
I tried to login with Xterm but it also doesn't work.
 
Some time ago, I had a similar problem, but then I could login with Xterm and init the desktop with xfce-panel ( or something like that ) and "magicaly" the problem was solved one day ( not sure if it is something related with this ).
 
I don't know what logs should I post to report this bug .

Log into a black console (via Ctrl+Alt+F1) and create a new user to see if the problem follows.
```
sudo adduser testuser
```
Once done, switch back to the login screen (via Ctrl+Alt+F7) and login with the testuser.

Regards
Iain

---

### Post by Rocafort8 on 2009-12-06
I  tried that but I still can't login.
I also noticed that the icon which appears in the login screen is different and is a command console icon ( when it worked the icon was the xubuntu logo ).

---

### Post by Rocafort8 on 2009-12-06
Ok, I found the problem.

The problem appears when I try to login and i'm very short of free space. I make apt-get autoremove to make some free space and then I logged without problems.

---

