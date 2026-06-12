---
title: "Do not start the desktop manager on boot"
date: 2009-09-02
forum: Desktop Environments
---

### Post by Plasma2002 on 2009-09-02
Ok, so I have ubuntu installed on a laptop with only 256 mb ram... as you can imaging, it sometimes starts to lag a little here and there.

The other thing is that I only use this machine remotely, aka through ssh.


I want to have ubuntu load so I can remote into it, but I dont need the window manager loaded on the local machine waiting for a login... its just sitting there taking up ram.


How can i make it so the machine only boots up to a command line? I dont want it to even start loading the window manager at all.

(I dont want to have to reinstall anything, like Server edition or something)

---

### Post by denver on 2009-09-02
Try this:

```
update-rc.d -f gdm remove
```

this should remove gnome display manager from startup. You should get a text mode login prompt.

Good luck!

---

### Post by Plasma2002 on 2009-09-02
Would i have to entireley remove it? I mean, if thats the only option, then ill do it.... 

but i was thinking that maybe if some day i really am in front of the machine, i can enter a command to start the manager if i wanted

---

### Post by i.r.id10t on 2009-09-02
The command mentioned above removes GDM from starting up in your runlevels.  You can still log into the console on the local machine and run startx to start a X session.

---

### Post by Plasma2002 on 2009-09-02
....oh!


well in that case..... thanks! :) its perfect

---

### Post by denver on 2009-09-02
You can add it back to your startup if you wish:

```
update-rc.d gdm defaults
```

to start gdm manually:

```
sudo /etc/init.d/gdm start
```

Have fun!

---

