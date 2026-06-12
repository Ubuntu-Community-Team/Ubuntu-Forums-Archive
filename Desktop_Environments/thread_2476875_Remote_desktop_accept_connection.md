---
title: "Remote desktop accept connection?"
date: 2022-07-10
forum: Desktop Environments
---

### Post by yuri-weinstein on 2022-07-10
I installed a fresh 20.04 and enabled desktop remote access.

However, every time as I try to connect I get on the desktop message to accept a new connection.

How can I enable all connections for all users or on per-user basis?

Thank you in advance!

---

### Post by TheFu on 2022-07-10
I use x2go instead.  Then just limit which users have access to ssh.

x2go has some caveats.  It doesn't like KDE or Gnome3+, so install and use a different DE - xfce, lxqt, mate or no DE, just a pure WM work great.
I haven't tested x2go on Wayland. It is based on X11, so ... er ... there might be a dependency on X11.

Because x2go is based on the NX protocol and all traffic goes through your normal ssh connection and credentials, it has similar security and mitigations as ssh. ssh is used by millions of admins daily to manage systems around the world, so it is probably secure enough.  

x2go feels 2-3x faster than VNC or RDP sessions.

So ... we gain better performance, better security, all just by using the x2go system.  There are commercial versions, if your company management likes to pay for stuff, but the F/LOSS version (x2go) doesn't have any arbitrary limitations like those commercial offers do.

---

