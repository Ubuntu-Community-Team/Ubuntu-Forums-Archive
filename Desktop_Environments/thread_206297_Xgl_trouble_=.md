---
title: "Xgl trouble =|"
date: 2006-06-29
forum: Desktop Environments
---

### Post by Jango on 2006-06-29
Hi guys!

I used that guide to install XGL [http://ubuntuforums.org/showthread.php?t=131267](http://ubuntuforums.org/showthread.php?t=131267)

I did every step so I assume that trouble is somewhere else then in this instruction sheet itself :D

Whenever I reboot (after I log in) the service doesn't work; if I try to start it manually, typing **gnome-window-decorator &  compiz --replace gconf &** in the terminal, screen splashes several times and a log in screen appears again =\

I'm lost, have no idea what to do... mmmmm, can anybody help me? :rolleyes: 

Thanks a lot!

---

### Post by Jango on 2006-06-30
Anyone?
Ok, I tried this just to check if it works [https://help.ubuntu.com/community/CompositeManager/InstallingCompiz](https://help.ubuntu.com/community/CompositeManager/InstallingCompiz)


I get the window w/o image 9black&white grid)
What I get in terminal is:

```

xauth:  creating new authority file /home/jango/.serverauth.7758
xauth:  error in locking authority file /home/jango/.Xauthority
xauth:  error in locking authority file /home/jango/.Xauthority
xauth:  error in locking authority file /home/jango/.Xauthority
xauth:  error in locking authority file /home/jango/.Xauthority

Could not init font path element /usr/lib/X11/fonts/TTF/, removing from list!
Could not init font path element /usr/lib/X11/fonts/OTF, removing from list!
Could not init font path element /usr/lib/X11/fonts/CID/, removing from list!
AUDIT: Fri Jun 30 09:44:37 2006: 7776 Xgl: client 1 rejected from local host
Xlib: connection to ":10.0" refused by server
Xlib: No protocol specified

[b]waiting for X server to begin accepting connections .
AUDIT: Fri Jun 30 09:44:39 2006: 7776 Xgl: client 1 rejected from local host
Xlib: connection to ":10.0" refused by server
Xlib: No protocol specified[/b]

..
AUDIT: Fri Jun 30 09:44:41 2006: 7776 Xgl: client 1 rejected from local host
Xlib: connection to ":10.0" refused by server
Xlib: No protocol specified

.X connection to :0.0 broken (explicit kill or server shutdown).

giving up.
xinit:  unable to connect to X server
xinit:  No such process (errno 3):  Server error.
xauth:  error in locking authority file /home/jango/.Xauthority

```

message in bold is the one that keeps on appearing untill u close the terminal window and kill xgl nest.

Does anybody know what's going on? :confused: 

Thanks a lot.

---

### Post by Jango on 2006-06-30
u know what? I LOVE ubuntu =))) I don't know WHY and HOW but now it works :) thanks a lot everybody.

---

