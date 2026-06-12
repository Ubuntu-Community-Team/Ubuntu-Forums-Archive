---
title: "Making a script to warn X users about shutdown"
date: 2008-12-28
forum: Desktop Environments
---

### Post by kurtkraut on 2008-12-28
When you run the shutdown command, users connected by terminal receive a warning:

```
[root@localhost ~]# shutdown +5 We are going to have a power outage.

Broadcast message from root (pts/0) (Sun Dec 28 03:06:24 2008):

We are going to have a power outage.
The system is going DOWN to maintenance mode in 5 minutes!

```

But X session users don't receive this kind of warning. This is a missing feature if you have remote users, thru **VNC** or **XDMCP** or **FreeNX**.

I'd like to make a script to warn X users too and I have **xmessage** and **zenity** in mind. But how would a script detect that a shutdown is being done or scheduled in the first place ?

---

