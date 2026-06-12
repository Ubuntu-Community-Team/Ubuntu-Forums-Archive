---
title: "SSH help"
date: 2006-09-04
forum: Desktop Environments
---

### Post by Trurl on 2006-09-04
Hi everyone,

  When I use SSH with XP and Solaris, it automatically forwards X11, allowing graphic displays, etc. However, I've been unable to replicate this behavior in Ubuntu. The only SSH functionality I've seen is when the 'ssh <user>@<server>' is used from a terminal. This gets me into my remote machine, and all text based functions work but there's no tunnelling support of X11. For instance, ghostview, pgplot, and mongo all crash when I attempt to display. SSH is essential to me, but without graphical support I'm stuck using XP. Any help would be much appreciated.

Thanks

Trurl

---

### Post by Jose Catre-Vandis on 2006-09-04
You have two choices, either forward X to your client, or set up a VNC session.

1. Forward X

```
ssh -X <user>@<server>
```
enter password
then type name of app
and you should get your remote app on screen

assuming you have open ssh server running on server

2. VNC with resumable sessions

Follow this howto:

[http://www.ubuntuforums.org/showthread.php?t=191564&highlight=VNC](http://www.ubuntuforums.org/showthread.php?t=191564&highlight=VNC)

---

