---
title: "Kubuntu + Xgl: shutdown freeze if splash is on"
date: 2007-01-31
forum: Desktop Environments
---

### Post by tanguyr on 2007-01-31
Hello,

I recently installed Xgl and Beryl on my laptop (Asus W2P, ATI X1700), and now i have noticed a problem when shutting down the machine (using the ctrl-alt-delete, "Turn off computer" method). Basically, the system shows the shutdown splash (which occasionally flickers, but the progress bar does not update) but nothing happens - i have to hit the power button to "really" shut down the machine. 

If i edit the GRUB menu line before booting and remove the "splash" parameter, then it works just fine (well, no splash obviously, but the machine shuts down promptly). 

To start with Xgl instead of the default X server, i edited my /etc/kde3/kdm/kdmrc [1] file and changed the lines:

```
ServerTimeout=15
to
ServerTimeout=30
```

and

```
ServerCmd=/usr/bin/X -br
to
ServerCmd=/usr/bin/Xgl -fullscreen :1 -ac -br -accel glx:pbuffer -accel xv:pbuffer
```

changing these back to their previous values - and all works perfectly (splash draws and updates, machine shuts down).

Any ideas? It's not a show stopper problem, but it does kinda put a crimp in my demos of my new "bling-enabled Linux desktop" ;-)

Regards,
/t

---

### Post by tanguyr on 2007-01-31
Guess i should have mentioned... 6.10 (edgy) i386... /t

---

