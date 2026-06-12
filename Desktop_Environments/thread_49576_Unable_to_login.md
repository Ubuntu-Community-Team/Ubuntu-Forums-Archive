---
title: "Unable to login"
date: 2005-07-16
forum: Desktop Environments
---

### Post by funman on 2005-07-16
I'm a relatively new Ubuntu user (or linux for that matter), I've been using it for about 2 weeks now, and falt the need to play some games, I got myself Point2Play for this, and they said I would need to update my ATI drivers to play, so I did.

The problem now is that the screen refresh rate is locked at 85Hz (which is making my sound make a wheexing sound, as it normally doesn't take more then 75), and whenever I attempt to login to my own account, it gives me a brown background with my mouse pointer for a little hwile, then i get a black background with a little X in the center, then it returns to the login screen.

Logging on as root work sperfectly (thank god i said for it to allow root logins).

The ATI drivers were installed using the Root Terminal on my user account.


I have just tried replacing the xorg.conf with my backup, and I can now change the refresh rate, but that is the only change.

---

### Post by evilghost on 2005-07-16
I think I'm confused, what's the problem?  When you said "... and I can now change the refresh rate, but that is the only change." it leads me to believe the issue is now resolved.  Specifically, what is the problem? :)

---

### Post by funman on 2005-07-16
the remaining problem is taht I can still not access my user, I am still logged on with the root user.

---

### Post by hydra on 2005-07-16
mmm at least this part u post [quote=funman]and whenever I attempt to login to my own account, it gives me a brown background with my mouse pointer for a little hwile[/quote]

is the same problem i have, and happens when i log out and then log in in my account....as i said i figure to solve this by ejecting the cd and then putting it back.......but i would really like a "remove hal bug" solution

anyways give it a try....

---

### Post by funman on 2005-07-16
I would love to do that...only that I have no cd in...

---

### Post by hydra on 2005-07-17
maybe trying to login to the console and load hal manager and see if its running

with **ps ax | grep**  hal and it should output something like : 

```
Ds 0:00 /usr/sbin/hald --drop-privileges
```

then if u get some errors u should try to kill Hal daemon :

**sudo killall hald**

and then start it with no daemon but verbose mode:

**sudo /usr/sbin/hald --daemon=no --verbose=yes**

and then all that text u receive u can check what the prob is or at least get an idea

---

### Post by funman on 2005-07-17
I do not get any errors, I get this:
> Ss     0:08 /usr/sbin/hald --drop-privileges

---

