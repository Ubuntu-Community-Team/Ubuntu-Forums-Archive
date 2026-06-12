---
title: "Xauthority not writeable"
date: 2008-10-26
forum: Desktop Environments
---

### Post by GrimRe on 2008-10-26
Hi,

I have a strange error that I can't seem to solve.

When I log into my server using PuTTY i get this message:

```
/usr/bin/X11/xauth:  /home/phil/.Xauthority not writable, changes will be ignored

```

And when I try and run a WINE application via VNC my desktop crashes and the remote desktop is closed. The only way to get back into it is the reboot the server.

This is the terminal output:

```
XIO: fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
after 77 requests (75 known processed) with 0 events remaining.
```

---

