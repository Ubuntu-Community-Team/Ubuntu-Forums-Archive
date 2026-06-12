---
title: "View everything with ssh"
date: 2008-03-06
forum: Desktop Environments
---

### Post by oddworld on 2008-03-06
I have been usning -X, the x11 forwarding to remotely run GUI programs.
Is there any way to remotely view the entire desktop using ssh?
Also, whats the command to transfer a single file using ssh?
Thanks

---

### Post by Nythain on 2008-03-06
remotely viewing the desktop via ssh alone, nope, not possible
what you can do is set up a vnc server on the computer, and tunnel a vnc connection through the ssh connection for security
look into x11vnc and tightvnc and vnc ssh for more info

---

