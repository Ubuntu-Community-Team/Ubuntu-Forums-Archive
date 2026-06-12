---
title: "How could I use ssh X forwarding and gdm instead of VNC?"
date: 2011-03-30
forum: Desktop Environments
---

### Post by WthIteh on 2011-03-30
Using "ssh -X user@server", it's easy to run programs on the server and see their GUI on the client machine. But I want to run the complete gdm on the server so it shows me Gnome login (for example on the vt8; accessible by Ctrl+Alt+F8 ) and when I login, I could work on remote machine while local display is in use via ssh X forwarding.
I know that usual solution is to use VNC for remote desktop functionality, but I want ssh X forwarding / gdm combination. Is it possible?
Also I tried "ssh -Xf user@server gdm" and running another X server on my local machine, but it fails sine there is ANOTHER gdm already running on the remote server (of course I do not want to kill it) and I could not find anyway for running two gdm instances on one machine too (at least till now).

Any solution is appreciated.

---

### Post by saivert on 2011-03-30
For Linux users:
Yes, you just need something like zephyr-server which runs a X server inside a window on top of your existing X session.

For windows users:
Use Xming from Windows with a root window and then launch gdm from within putty *or your favorite ssh client) with X11 forwarding enabled.

---

