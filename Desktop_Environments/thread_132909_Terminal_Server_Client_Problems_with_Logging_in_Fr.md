---
title: "Terminal Server Client Problems with Logging in From a Multi Head Machine"
date: 2006-02-19
forum: Desktop Environments
---

### Post by limewolf on 2006-02-19
I have two machines, one is a three monitors system, the other is a single monitor system. Both run Breezy. I use the three monitor system for work and the single monitor system is mostly a file server, but is also a backup work machine (hence the reason it has X/Gnome). Both machines use nvidia gfx cards and the nvidia drivers.

I can login to the single monitor system from other machines on my network, via XDMCP and the Terminal Server Client in Gnome, but it does not work when I try to login via the three monitor machine. I get an error along the lines of this:

```
X Error of failed request: Bad value (integer parameter out of range for  operation)
Major opcode of failed request: 78 (X_CreateColormap)
Value in failed request: 0x0
Serial number of failed request: 24
Current serial number in output stream: 88
```


Now, if I edit my xorg.conf file and turn off the other two monitors - commenting out the second two screen options as below...

```

Screen      0  "Screen0" 0 0
#Screen      1  "Screen1" RightOf "Screen0"
#Screen      2  "Screen2" RightOf "Screen1"

```

...it works fine - I can login just like on any other machine. If I try to login to other machines on the network when I have the three monitors running I get the same error as above, only turning them off in the xorg.conf file cures the problem.

Can anyone tell me if this a known problem and/or if there is anything I might try and do to solve it?

Cheers.

---

