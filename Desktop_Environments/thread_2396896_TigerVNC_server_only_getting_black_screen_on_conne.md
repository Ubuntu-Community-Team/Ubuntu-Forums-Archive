---
title: "TigerVNC server only getting black screen on connect"
date: 2018-07-22
forum: Desktop Environments
---

### Post by dearzac on 2018-07-22
*I have also posted on the developer's discussion board, but (1) in case it's an Xubutnu issue and not a TigerVNC issue and (2) so I can ask a bigger community, I am also posting here.*

I did a fresh install of Xubuntu Desktop 18.04 via DVD on a test machine. I then used the generic 1.9.0 binaries for TigerVNC server. I can connect with no problem and can see the desktop just fine.

*The reason I used the generic files is that the Ubuntu repo is stuck back on 1.7.0, and the bintray files from the dev doesn't include an official 18.04 compatible .deb file yet.*

When I repeated the exact same install procedure on my production machine, I connect with no errors, but all I see is black (no desktop).

*The production machine is not from the Xubuntu Desktop DVD. It's from the 18.04 alternative server DVD (so I could use the RAID wizard) and then Xubuntu desktop added after the fact with: sudo apt-get install xubuntu-desktop*

I did a bunch of searching and found a different xstartup suggested here instead of the default created the first time vncserver is run: https://wiki.archlinux.org/index.php/Vncserver
```
#!/bin/sh
unset SESSION_MANAGER
unset DBUS_SESSION_BUS_ADDRESS
exec startxfce4
```

With this xstartup, I don't get black (I am able to see the desktop), but the log file has tons of errors (attached).

I'm assuming the default xstartup is fine (since it was on the other machine), and that I have something else going on.

---

