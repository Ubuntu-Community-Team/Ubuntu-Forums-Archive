---
title: "Running remote application causes X server to reject local applications"
date: 2009-01-28
forum: General Help
---

### Post by dallingham on 2009-01-28
Since 8.10, I've had a problem with running certain applications remotely. I think the common denominator is Java.

If I ssh into a server, and run a particular application (Xilinx's ISE program), I can no longer launch applications local to my desktop.

$ ssh -X server

server$ ise

server$ exit

$ gnome-terminal
No protocol specified
Cannot open display: 
Run 'gnome-terminal --help' to see a full list of available command line options.

$ xterm
No protocol specified
xterm Xt error: Can't open display: :0.0

No new windows can be opened until the X server is restarted. Other applications run remotely do not have the same effect.

This problem did not exist in previoius Ubuntu versions, and does not exist in Red Hat 4 or 5.

---

### Post by dallingham on 2009-01-28
Oddly enough, it appears that using

 $ ssh -Y server

prevents the local display from having this problem. I don't understand why.

---

