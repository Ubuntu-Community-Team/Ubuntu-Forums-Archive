---
title: "Remote access"
date: 2016-12-27
forum: Desktop Environments
---

### Post by welshmark2 on 2016-12-27
I have been trying to get remote access to my Ubuntu computer from a windows 10 pc using tight vnc but all I get after logging in is a black screen.
If i connect a screen to the Ubuntu computer at startup then all is fine but that defeats the object for me. I'm using tight vnc on my windows PC. I'm not worried about security as its not connected to the internet I just wat to access it remotely with a gui.

Any ideas where I'm going wrong or what alternative I can use to get a gui?

My Ubuntu version is 16.04.1, Gnome 3 (I think), vino 3.8.1

Have I missed anything?

Many Thanks

---

### Post by TheFu on 2016-12-29
* ssh for remote access.
* sftp/scp/rsync for remote file transfers. These are built on ssh and included with the ssh-server package.
* x2go for remote desktop needs. This uses ssh for authentication. The server is only on Linux, but there are clients for the 3 main desktop OSes.  x2go is based on NX, which feels about 2-3x more efficient than VNC. The x2go website has install instructions for the server and the client. Use their PPA.  

As you can see, everything starts with ssh. Setup ssh-keys to make it more secure AND more convenient.  
[B]
Setup ssh first. This is important.[/B]

On the same LAN, you can use normal, built-in X/Windows.  There is a mode for ssh that automatically sets up X-Forwarding correctly. [http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications](http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications)

Ah. I see you have Windows. Might be easiest to just run a tiny VM and use that for all Linux GUI access.  TinyCore is, er, .... tiny and runs extremely fast. Using it with **ssh -X** to the Linux system will get GUI programs running on the remote machine to display locally.

---

