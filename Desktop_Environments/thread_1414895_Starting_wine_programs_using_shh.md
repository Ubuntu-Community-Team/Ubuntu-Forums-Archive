---
title: "Starting wine programs using shh"
date: 2010-02-24
forum: Desktop Environments
---

### Post by gased on 2010-02-24
Hi folks,
I want to do this remotely. Open a session  (nx,vnc I don't really care as far as it is a session) and then start utorrent.exe using wine.
Is that possible?
Because by just typing on ssh sudo wine utorrent.exe it can't start as there is no session to host it.

---

### Post by Hero of Time on 2010-02-25
You can't really start things remotely like that. You have to either connect to the existing GUI session like with VNC, or set the remote display option with ssh. To get your program to run on your local machine from the remote one, use 'ssh -X <machine>' to log in, then run the program you want. I'm really wondering why you want to use uTorrent on Linux, there are tons of alternatives, like Transmission, Deluge and others. Transmission for example even has a daemon version and web interface.


And really, DON'T EVER run Wine as root!

---

