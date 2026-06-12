---
title: "VNC - File Manager Only"
date: 2017-02-23
forum: Desktop Environments
---

### Post by Geoff_Lane on 2017-02-23
Folks,

I've previously used tightvncserver via an ssh tunnel on two machines remotely - both have ended up giving me a file manager ONLY :mad:

I have not knowingly altered anything.

The machine I am currently trying to access is a RaspberryPi running Ubuntu-Mate

My xstartup file shows as follows;

```
#!/bin/sh

def
export XKL_XMODMAP_DISABLE=1
unset SESSION_MANAGER
unset DBUS_SESSION_BUS_ADDRESS
 
gnome-panel &
gnome-settings-daemon &
metacity &
nautilus &
gnome-terminal &
gnome-session &



```

Any suggestions appreciated.

Geoff

---

### Post by Geoff_Lane on 2017-02-23
> **Geoff_Lane said:**
> Folks,


Any suggestions appreciated.

Geoff

Resolved - just needed to add the following to my xstartup file;
```
mate-session &
```

Geffers

---

### Post by oldrocker99 on 2017-02-24
You solved your problem, so please use the Thread Tools to mark this thread as [SOLVED].

---

### Post by Geoff_Lane on 2017-02-24
> **oldrocker99 said:**
> You solved your problem, so please use the Thread Tools to mark this thread as [SOLVED].

I did look, cannot find 'Thread Tools'.

Geffers

Just found 'Thread Tools'

---

