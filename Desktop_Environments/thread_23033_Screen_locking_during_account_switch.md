---
title: "Screen locking during account switch"
date: 2005-03-30
forum: Desktop Environments
---

### Post by gylf on 2005-03-30
I have a second account setup for my wife, who likes to have her games and email on the desktop.  It works very well, since she can go to "System Tools" then "new login" and get to her desktop, without distrubing any windows I may have left open.

The problem is that sometimes either the computer or she goofs and she ends up leaving my account and then going back to my account.  At that point she has no choice but to put in my password (which she can never remember  #-o )
Once the "locked screen login" comes up, is there a way to revert back out to the login screen (so that she can login with her username and password)?  She's been resorting to rebooting the computer, a solution I'm not real fond of!

EDIT: I've also noticed that occationally just going to "new login" can cause the computer to lock the current account and not bring up the login screen.  I believe this happened when I updated without a restart, but I'll continue looking into it.

---

### Post by TravisNewman on 2005-03-30
ctrl+alt+f8 should bring up the second login, and if you want to get back to the first, ctrl+alt+f7

---

### Post by gylf on 2005-03-30
[QUOTE=panickedthumb]ctrl+alt+f8 should bring up the second login, and if you want to get back to the first, ctrl+alt+f7[/QUOTE]
That will help a lot... actually I feel stupid for not having tried that.

However, how can it be used when there is only one account currently logged in (mine), and its locked?  If I ctr-alt-F8 it'll just bring up a flashing cursor.  Is there a way to bring up a new login (maybe by logging into the prompt with ctr-alt-F1 and running a command)?

---

### Post by ntd on 2005-03-30
If you do a ctrl+alt+f1, sign on as the secondary user (ie your wife), the type:

startx -- :1

It will start a new xserver that you can access with ctrl+alt+f8...this way you can switch between you (f7) and here (f8 ) with none of that pesky screenlocking...this is what I setup for my wife and I

---

### Post by ReiKn on 2005-07-19
[QUOTE=ntd]If you do a ctrl+alt+f1, sign on as the secondary user (ie your wife), the type:

startx -- :1

It will start a new xserver that you can access with ctrl+alt+f8...this way you can switch between you (f7) and here (f8 ) with none of that pesky screenlocking...this is what I setup for my wife and I[/QUOTE]

If I try this I get an error message saying:

> Fatal server error:
Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again.

---

