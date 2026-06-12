---
title: "Computer hangs on logout"
date: 2008-05-21
forum: Desktop Environments
---

### Post by kooldino on 2008-05-21
I cannot successfully log out of my 8.04 KDE sessions.  When I try to, it will eventually unload the interface and I will have a black screen with no cursor or anything. 

If i do a hard reset on the machine and log back in, my previous session isn't saved.  It keeps restoring a session for 4 days ago.  

Help!

---

### Post by kooldino on 2008-05-22
Anyone?  What procedures are operated upon logout from kde?

---

### Post by kooldino on 2008-05-22
Hello?

---

### Post by NightwishFan on 2008-05-22
I am not sure how to fix, but as a temp solution, try this command to reboot.
```
sudo reboot now
```

---

### Post by chandra on 2008-05-23
> **kooldino said:**
> I cannot successfully log out of my 8.04 KDE sessions.  When I try to, it will eventually unload the interface and I will have a black screen with no cursor or anything. 

If i do a hard reset on the machine and log back in, my previous session isn't saved.  It keeps restoring a session for 4 days ago.  

Help!

Perhaps these links might help:

[https://bugs.launchpad.net/ubuntu/+bug/230817](https://bugs.launchpad.net/ubuntu/+bug/230817)

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/230624](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/230624)

---

### Post by kooldino on 2008-05-23
> **NightwishFan said:**
> I am not sure how to fix, but as a temp solution, try this command to reboot.
```
sudo reboot now
```

Rather than logging out, if I go to a terminal window and type ```
sudo poweroff
``` the screen will go black...it will just sit there for 20 seconds, and the the kubuntu reverse progress bar will appear and the power will eventually turn off.  Something still doesn't feel right about it, and I'd like to know why I can't log out or shut down via the gui.

---

### Post by kooldino on 2008-05-23
> **chandra said:**
> Perhaps these links might help:

[https://bugs.launchpad.net/ubuntu/+bug/230817](https://bugs.launchpad.net/ubuntu/+bug/230817)

Nice find!  I have this issue as well!

> [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/230624](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/230624)

...and that's the bug I'm talking about.  So it's not just me.  It appears to have no resolution just yet. :-/

---

### Post by ricardisimo on 2008-06-11
I've noticed this problem when I logout as the sole user (as I used to do on Ubuntu). One expects the login screen to pop up, but no - just black screen. However, if I have two or more user accounts active, then I do, in fact, get the login screen (which is what it should also do in Ubuntu, by the way, rather than going straight to the last-opened session's locked screensaver... but that's a separate issue.)

Am I wrong? Is this not the same problem you are experiencing? Do you have another account with which you could test this out?

---

### Post by kooldino on 2008-06-12
The bug linked above describes the issue I had.

I'm now running an NVidia card and the issue is gone.

---

### Post by penguinbreath on 2008-06-12
I am having the same problem with logging out in Kubuntu 8.04. Screen often goes completely black.

Sometimes I can successfully log out. It seems it works when no applications are open, but I am still not sure about this.

---

