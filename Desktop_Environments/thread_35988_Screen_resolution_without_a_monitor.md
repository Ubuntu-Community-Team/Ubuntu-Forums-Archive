---
title: "Screen resolution without a monitor"
date: 2005-05-21
forum: Desktop Environments
---

### Post by ShaneAu on 2005-05-21
I only access Ubuntu via VNC, it's hardley ever connected to a monitor (only when I can't connect from other computers in my LAN).

The problem is, the resolution gets stuck on 640x480 when I don't have a monitor plugged in, when I do it will default at a 1280x1024, I want it to stay at about 1024x768.

I don't know what to do, I've done heaps of searching on Google and these forums but can't find an answer, I've fiddled around with /etc/X11/xorg.conf, but no success.

Any ideas?

- Shane.

---

### Post by mnorman4 on 2005-08-07
Anybody know the solution for this one?

I too have a machine that doesn't have a monitor connected most of the time that I VNC into.  On bootup it defaults to 640x480.  I have removed the lower resolution options from my xorg.conf file, but that didn't solve the problem.

---

### Post by theFUZZYpickle on 2005-10-31
i also have this problem ... can anyone help?

---

### Post by Franko30 on 2006-01-29
Hi,

First: Sorry for the crosspost, but resolving this was just too frustrating for me and I want people to find this in all the other unresolved "help VNC resolution" threads, too.

I didn't want to go for the modelines as described in

[http://www.ubuntuforums.org/showthread.php?p=690202](http://www.ubuntuforums.org/showthread.php?p=690202)

and found a solution that works for me:

In the **device** section of the **xorg.conf** I changed the driver to

```
Driver		"vesa"
```

and finally my headless Ubuntu setup starts up in the required resolution of 1024x768 I entered in the xorg.conf file - which makes using this machine with VNC a bit nicer than with 640x480. :-)

And we don't need a fancy 3D driver on a machine accessed via VNC - do we?

It worked on two machines (running climateprediction.net with BOINC) with different graphics adapters.

I hope it might work for others, too...

Franko30

---

