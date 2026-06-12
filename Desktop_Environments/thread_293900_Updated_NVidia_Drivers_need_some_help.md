---
title: "Updated NVidia Drivers need some help"
date: 2006-11-05
forum: Desktop Environments
---

### Post by Beamerboy on 2006-11-05
Hi,

I just updated my nvidia drivers via synaptic and after restarting xauth is being a pain.

I normally have two xservers running, one with my main desktop with xinerama and one with cedega in single monitor mode.  Below is how I used to start the second xserver:

```

sudo xinit /usr/bin/cedega -- :1 -config xorg-games.conf

```

[xorg-games.conf being a second config file with xinerama disabled and only one monitor turned on.]

Now when I try and run it, I get xauth telling me off:

```

AUDIT: Mon Nov  6 02:01:48 2006: 6574 X: client 1 rejected from local host
Xlib: connection to ":1.0" refused by server
Xlib: No protocol specified

```

I have tried:

```

xhost +localhost

```
and
```

xhost +hostname

```

But I am still getting the same errors.  Any help appreciated.  Also if someone could instruct me how to use xauth cookies so I don't have to run the second xserver as root I would appreciate it.

Beamerboy

---

