---
title: "VNC over SSH in hardy"
date: 2008-05-07
forum: Desktop Environments
---

### Post by rmccarri on 2008-05-07
Hi,
I have an Ubuntu Desktop version 8.04 LTS Hardy install.  Everything is running really well, but I have been unable to get VNC over an SSH tunnel to work.  I am trying to connect to my Ubuntu desktop from a Windows laptop via PuTTY and TightVNC.  If I open port 5901 on my router (for VNC desktop :1), I can connect fine using my ip directly through the TightVNC client on my laptop.  Obviously, this is not ideal since it opens an unencrypted connection.

If I close that port and try to connect through an SSH tunnel via PuTTY using L5900 localhost:5901 or L5901 localhost:5901 and then connect to localhost:1 or localhost:5901 in TightVNC, no dice.  This works quite well with some other Linux and Windows computers that I have configured.  Is there some place where you have to enable tunneling through SSH in hardy?  Has anyone else had the same problem?
Any help would be greatly appreciated.
Rob

---

