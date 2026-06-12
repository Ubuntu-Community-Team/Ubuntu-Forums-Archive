---
title: "World's shortest startup script?"
date: 2008-12-11
forum: General Help
---

### Post by gvanto on 2008-12-11
Hey I've got just one line:

sudo /etc/init.d/ssh start

which I'd like to run each time I start Kubunutu.

Where is the best place to put a script or something for this to happen?


Many thanks
Gerry
newbie

---

### Post by wizard10000 on 2008-12-11
> **gvanto said:**
> Hey I've got just one line:

sudo /etc/init.d/ssh start

which I'd like to run each time I start Kubunutu.

Where is the best place to put a script or something for this to happen?

Are you sure it's not autostarting already?

There are quite a few places to start it but the first place I'd look is in System --> Administration --> Services to see if you can just tick a box to make the sshd autostart.

Another idea is to install Boot Up Manager - 

```
sudo apt-get install bum
```

which is IMO a little better interface than the services applet.  Another trick is to run sysv-rc-conf but that's a runlevel editor and you kinda need to be careful in there.

Last, I guess you could call it from /etc/rc.local - that script runs as root and sudo is unnecessary there.

You could also stick a script in ~/.kde/Autostart

Hope this helps -

---

