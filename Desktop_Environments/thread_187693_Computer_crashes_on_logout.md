---
title: "Computer crashes on logout"
date: 2006-06-03
forum: Desktop Environments
---

### Post by Lil_Eagle on 2006-06-03
I have a problem.  Every time I log out with Gnome, my computer crashes.

I can successfully log out and back in with KDE.

I have the problem with both desktops that if I open a virtual terminal, when I come back to X, my system crashes.  I also can't lock one session and start another without it crashing.

I have the feeling that it has something to do with my video card as usually when this happens I see garbage on the screen, but I am using the latest ATI fglrx drivers.  Could it be the X.Org 7.0?

Has anyone else heard of such a problem?  I had no problems at all with Breezy, and unless I can get this recified, I have no other option but to downgrade, because this computer is for the whole family, and I have to be able to log out and back in as a different user.

Everything else is working fine, and I commend the efforts of the developers in creating the Dapper Drake release, but unless I can get this recified, I will be forced to downgrade.

Reference:

```
joe@ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 2.0.5814 (8.25.18)
```

---

