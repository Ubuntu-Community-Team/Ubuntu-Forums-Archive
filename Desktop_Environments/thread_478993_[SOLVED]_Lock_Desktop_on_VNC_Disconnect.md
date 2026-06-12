---
title: "[SOLVED] Lock Desktop on VNC Disconnect"
date: 2007-06-19
forum: Desktop Environments
---

### Post by bobpaul on 2007-06-19
On Windows, most VNC Servers (TightVNC and RealVNC for sure) have an option where the screen is locked when the last user leaves the session.

Is it possible to do this on Ubuntu? Would I need to replace the default VNC Server? How would I go about doing that?

My network connection is sometimes flaky, and I can't always lock the screen before disconnecting from the machine. It'd also be nice if I could turn off the monitor on connect so nobody locally can see what I'm doing when I am connected, but perhaps that's another thread.

Thanks,
~Bob/Paul~

---

### Post by bobpaul on 2007-07-09
Since asking this question I broke my install beyond repair and installed Kubuntu, as I only had an *old* Ubuntu CD lying around. I'm not sure how to do this in Gnome, but this should provide ideas to anyone making the attempt. 

The KDE wiki describes [locking the screen from the command line]("http://wiki.kde.org/tiki-index.php?page=Tips%20and%20Tricks&pagenum=12").
This thread describes [using x11vnc instead of kfrb on KDE]("http://ubuntuforums.org/showthread.php?t=196572")

I modified my ~/.kde/Autostart/x11vnc script to read:
```
#!/bin/bash
while [ true ]; do /usr/bin/x11vnc -rfbauth ~/.vnc/passwd; dcop kdesktop KScreensaverIface lock; done &
```

Notice I removed the -forever option from x11vnc. This causes x11vnc to terminate after the last connection closes. When that happens, the deskop is locked and x11vnc is restarted.

---

