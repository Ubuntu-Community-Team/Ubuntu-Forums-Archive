---
title: "headless Ubuntu"
date: 2012-03-12
forum: Desktop Environments
---

### Post by hitime on 2012-03-12
Hey all,

I'm looking for some info on setting up a headless Ubuntu desktop.  I do not want to have the system automatically login (not sure if default screen sharing in 12.04 needs this) but I really dont want to ssh in and start and a VNC session everytime I want to login.  I would really like to be able to just open and session, see the standard login and go from there if possible, does freeNX do this?  I'm going to be using the box for video crunching and some other tasks that just need the CPU power so (GUI would be preffered).  Any help is appreciated.

Thanks,
hitime

---

### Post by JRV on 2012-03-12
You can do it with XDMCP.

First you need to enable XDMPC on the headless machine.

```

gksudo gedit /etc/lightdm/lightdm.conf

```

Add the following lines to the bottom of the file:

```

[XDMCPServer]
enabled=true

```

and reboot.

Now add Xephyr to every machine you wish to log in from:

```

sudo apt-get install xserver-xephyr

```

To log in the command I use is:

```

Xephyr :1 -query HOSTNAME -fullscreen -once

```

The X in Xephyr must be capitalized.

Sometimes it will not let you in because a screen is in use.
If this happens change :1 to :2 or :3.

---

### Post by hitime on 2012-03-12
Thank you, I'll have to take a look at this.  Any issues with screen resolution limitations or anything?

---

### Post by JRV on 2012-03-12
> **hitime said:**
> Thank you, I'll have to take a look at this.  Any issues with screen resolution limitations or anything?

It works best with Unity 2d, 3d can get rather net-intensive. 

I usually use fullscreen but any resolution supported by the client running Xephyr will work. 

For more options:
```

Xephyr --help

```

---

