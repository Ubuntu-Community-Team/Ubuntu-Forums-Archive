---
title: "Cannot log in"
date: 2008-09-13
forum: Desktop Environments
---

### Post by Borsook on 2008-09-13
Hi, My Xubuntu worked fine yesterday and today I cannot login, it throws my out under 10 secs, here is the error log:
```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
_IceTransmkdir: ERROR: (l)stat failed for /tmp/.ICE-unix (13)
_IceTransSocketUNIXCreateListener: mkdir(/tmp/.ICE-unix) failed, errno = 13
_IceTransMakeAllCOTSServerListeners: failed to create listener for local
xfce4-session: Unable to establish ICE listeners: Cannot establish any listening sockets
```

---

### Post by Pro-reason on 2008-09-13
I don't know what is happening there.

Can you log in via the text terminal (Ctrl-Alt-F1)?  If so, you can try creating a new user (“sudo adduser johndoe”).

---

### Post by Borsook on 2008-09-13
> **Pro-reason said:**
> I don't know what is happening there.

Can you log in via the text terminal (Ctrl-Alt-F1)?  If so, you can try creating a new user (&#8220;sudo adduser johndoe&#8221;).

I'll try that. First I thought it was something in x11-common but it appears to be intact, so tmp/.ICE-unix should be created at startup... BTW just to be on the safe side I tried chmod 177 /tmp/.ICE-unix as root but it displays I don't have a permission to that folder, and I can't chown it either... I may be rambling, it's just the only line from the error log that I understand :)

PS> Logging as different user gives the same result

---

### Post by Pro-reason on 2008-09-13
If you don't have permissions, do “**sudo** chown” or “**sudo** chmod” on it.

---

### Post by Borsook on 2008-09-13
> **Pro-reason said:**
> If you don't have permissions, do “**sudo** chown” or “**sudo** chmod” on it.

yes of course, this is what I did, logged to the terminal as root, run those with sudo and still got permission error...

---

### Post by Pro-reason on 2008-09-13
> **Borsook said:**
> yes of course, this is what I did, logged to the terminal as root, run those with sudo and still got permission error...

Is “sudo” failing generally?  Can you, for example, do “sudo ls”?

---

### Post by Pro-reason on 2008-09-13
Is /tmp/ on the same partition as /?

Can you chmod other files in /tmp/?

Can you install another desktop environment (Xfce, Openbox...) and log in to it?

---

### Post by Borsook on 2008-09-13
> **Pro-reason said:**
> Is /tmp/ on the same partition as /?

Can you chmod other files in /tmp/?

Can you install another desktop environment (Xfce, Openbox...) and log in to it?

Sudo is working fine with the only exception of that folder, tmp is indeed on the same partition as /, XFCE is installed it being Xubuntu :) installing any other DE is not a good idea, it's a very old PC with a 2.2 GB HDD.

---

### Post by Pro-reason on 2008-09-13
> **Borsook said:**
> Sudo is working fine with the only exception of that folder, tmp is indeed on the same partition as /, XFCE is installed it being Xubuntu :) installing any other DE is not a good idea, it's a very old PC with a 2.2 GB HDD.

Openbox and Fluxbox are extremely light (much more so than Xfce), so there would probably be room, even on your machine.

---

