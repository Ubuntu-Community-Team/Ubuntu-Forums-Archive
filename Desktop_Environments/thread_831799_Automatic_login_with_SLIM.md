---
title: "Automatic login with SLIM?"
date: 2008-06-17
forum: Desktop Environments
---

### Post by IamAcoconut on 2008-06-17
How to make Slim (Simple Login Manager) automatically log a specified user at startup? To show nothing on boot, just log in, like GDM can do. 
I spent some time searching this forum for answer, to no avail.
I usually run Openbox-Gnome, or simply Openbox, but it doesn't make a difference to Slim, it shouldn't, I figure.

---

### Post by LeSid on 2008-06-17
After installing slim with apt-get, just run

```
sudo dpkg-reconfigure slim
```

Slim kicks off flixbox on my system without the need of reconfiguring slim.conf :-)

---

### Post by IamAcoconut on 2008-06-19
What I want to accomplish is to see **no login screen** at boot, no sign of any login/display manager, just have my user logged in automatically without being asked for a password. That's what I had with GDM, but it was such a freaking waste of time anyway just waiting for GDM to finish it's job (Gutsy's issue), that I couldn't stand [the beige screen!] and got rid of it. 
> **LeSid said:**
> After installing slim with apt-get, just run
```
sudo dpkg-reconfigure slim
```
And what does that change? I already have Slim as a default DM. I changed Slim.conf, so that my username gets loaded automatically, I don't have to type it, but that's all. 

Is what I try to accomplish impossible with Slim? What lightweight DM could serve that purpose than?

---

### Post by eriqjaffe on 2008-06-19
If you want to auto-login with no trace of a login manager, why have a login manager at all?

[http://ubuntuforums.org/showthread.php?t=727947](http://ubuntuforums.org/showthread.php?t=727947)

Take a look at the third post in that thread, it may give you some ideas.

---

