---
title: "Icewm won't run after a logout"
date: 2011-03-21
forum: Desktop Environments
---

### Post by frankzen on 2011-03-21
Running an up-to-date Ubuntu Natty - IceWm will run IF I go into it from GDM after a reboot. If I logout and try to go back into Ice it simply returns to the GDM prompt. I have checked all the logs and nothing relevant appears in any of them. I re-installed Icewm but no change.
Any ideas?

---

### Post by frankzen on 2011-03-23
Nobody ??

---

### Post by bobb40 on 2011-05-04
Thanks for the tip on how to run Icewm in Natty - I'd been trying without any success at all.  But I don't know how to get it to run after a logout - will post if I find out.

---

### Post by frankzen on 2011-05-04
I have since discovered that it will run, IF you change the desktop file to exec icewm, not icewm-session. But then you lose all xsessions abilities, such as running a startup file to start other processes with icewm.
So the problem appears to be in icewm-session.

---

### Post by prasadbrg on 2011-07-27
Hi Frankzen,
  I've been having the same issues that you've been having. How exactly do you change the 'desktop file' to exec icewm and not icewm-session?
Thanks in advance!

Cheers,

G

EDIT: Figured it out myself:
```
sudo gedit /usr/share/xsessions/IceWM.desktop
```
Change the line```
Exec=/usr/bin/icewm-session
```to
```
Exec=/usr/bin/icewm
```

Thanks anyways!

---

### Post by frankzen on 2011-07-28
I see you figured it out yourself :) Now to figure out why! Well it's apparently because Gnome runs a session manager, and so icewm-session won't run after that.

---

### Post by prasadbrg on 2011-07-28
> Now to figure out why! Well it's apparently because Gnome runs a session manager, and so icewm-session won't run after that. :) I do hope this issue is resolved at the earliest...
:popcorn:

---

### Post by frankzen on 2011-10-15
> **prasadbrg said:**
> :) I do hope this issue is resolved at the earliest...
:popcorn:

Still not resolved. October 2011 !!!

---

