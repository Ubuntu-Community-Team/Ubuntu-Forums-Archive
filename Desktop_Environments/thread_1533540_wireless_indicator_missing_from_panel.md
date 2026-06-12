---
title: "wireless indicator missing from panel"
date: 2010-07-18
forum: Desktop Environments
---

### Post by Alex Flint on 2010-07-18
Hi there,

Sometimes when I start my computer the wireless indicator in the top-right part of my screen is missing and I don't know how to add it back. Clicking "Add to panel..." doesn't seem to lead to anything useful. My wireless card is working fine and after restarting my computer a few times the icon usually appears and I can connect to wifi networks without trouble.

Also, how would I connect to a wireless network _without_ using this icon?

Cheers,
Alex

---

### Post by iponeverything on 2010-07-18
You can bring back Network manager from the command like so:

```

nm-applet
disown %1 
exit

```

Configuring the interface though /etc/network/interfaces will make come up automatically at boot and it will no longer managed by Network Manager.


Setting up a wireless connection though interfaces can be a tiny bit complex but is not too hard.

see:
[http://ubuntuforums.org/showthread.php?t=1121741](http://ubuntuforums.org/showthread.php?t=1121741)
or
[http://wwww.ubuntuforums.org/showthread.php?t=1454064](http://wwww.ubuntuforums.org/showthread.php?t=1454064)

---

### Post by Mrsongs on 2010-07-19
> **iponeverything said:**
> You can bring back Network manager from the command like so:

```

nm-applet
disown %1 
exit

```

Configuring the interface though /etc/network/interfaces will make come up automatically at boot and it will no longer managed by Network Manager.


Setting up a wireless connection though interfaces can be a tiny bit complex but is not too hard.

see:
[http://ubuntuforums.org/showthread.php?t=1121741](http://ubuntuforums.org/showthread.php?t=1121741)
or
[http://wwww.ubuntuforums.org/showthread.php?t=1454064](http://wwww.ubuntuforums.org/showthread.php?t=1454064)
I had the same problem and tried the code, and got this message:
An instance of nm-applet is already running.

** (nm-applet:2691): WARNING **: <WARN>  constructor(): Couldn't initialize the D-Bus manager.

so Network manager is running, but there is no icon, no signal indicator and no way to switch networks as in a fresh install. Any ideas? Thanks.

---

### Post by iponeverything on 2010-07-19
try killing off nm-applet first.

```
killall -v -9 nm-applet
```

---

