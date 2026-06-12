---
title: "recovering Unity in my session though it works in guest session"
date: 2014-09-06
forum: Desktop Environments
---

### Post by ray field on 2014-09-06
I've been wrestling trying to get Unity working again on my Chromebook using Chrubuntu as a result of a few things that blew up at the same time. About a month ago, I had shut down after turning off Network Manager -- I didn't need it trying to connect to a wifi network, and I guess in my impatience, turned off networking instead of just the wifi. Somehow my Unity session got corrupted so that after login, my screen was blank -- no panel, no launcher -- just the single folder that I have on my desktop. Worse yet, I couldn't figure out how to get wifi working from a terminal session -- so I decided to give up and buy a USB ethernet dongle (this Acer Chromebook doesn't have an ethernet port). I installed xfce -- which I wasn't very thrilled about, mostly I suppose because I've gotten so accustomed to using Unity.

Anyway, all that is background to what I hope will be a relatively simple problem to solve:

Just now I logged into a Guest Session using Unity, and much to my surprise, the standard Unity desktop started. I switched on Networking from Network Manager, and wonderful to say, my wifi connected automatically. Then I shut down and re-logged into Unity on my own account, and although the Unity desktop was still crippled, networking and wifi apparently are working fine -- I tried installing a package in an Ctrl-Alt F2 terminal session and it worked just fine.

So, what do I have to do to get Unity working again in my own session? I'd like to keep those old settings back but will start from scratch if it will make things easier.

I will add that when I log out of the Guest Session and then back into my own crippled session, I can see the login process hanging: Ctrl-Alt F1 shows me a terminal screen saying

```
Ubuntu 14.04 LTS Cottard tty1

Cottard login: *Starting Bridge socket events into upstart
*Starting Bridge socket events into upstart

```

---

### Post by ray field on 2014-09-08
umpitty ba

---

### Post by CantankRus on 2014-09-08
Try this.
Log into your unity session.
Go to a tty... ctrl+alt+F1
Log in and run....
```
DISPLAY=":0" dconf reset -f /org/compiz/ && setsid unity
```
Give it 30 seconds or so to run and then switch back to unity.... ctrl+alt+F7

When I did this there was no logout menu.
Open a terminal and run
```
kill -9 -1
```
and log back in.

---

### Post by ray field on 2014-09-08
many thanks, 'tank! that did it!

---

### Post by CantankRus on 2014-09-08
You **Can tank Rus** ;)

---

