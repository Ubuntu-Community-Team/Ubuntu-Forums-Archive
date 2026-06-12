---
title: "How to configure VNC sever in Ubuntu 15.04"
date: 2015-08-01
forum: Desktop Environments
---

### Post by yadav-vml on 2015-08-01
Hi.. I want to configure VNC server in my Ubuntu 15.04 so i can access it through other computers.

I have followed the below steps:

sudo apt-get install tightvncserver
vncserver

i have already configure VINO.

When i try to connected it through other computer it shows "Failed to connect".

How can i fix it.

Thanks in advance.

---

### Post by TheFu on 2015-08-01
Sorry, don't know much about vnc except that it is much harder to use than it should be. You need to setup a startup script for the **vncserver** to fine which determines which DE and/or window manager will be used.  3D DEs are a really bad idea.  There are other answers for this with extreme detail in these forums. Search a little and you'll find those.  I'll update with a link if I find it.
Found one:
[http://ubuntuforums.org/showthread.php?t=2258466&highlight=vnc+startlxde](http://ubuntuforums.org/showthread.php?t=2258466&highlight=vnc+startlxde) with lots of details.
Steeldriver's post #4 is good.

Or you could use **x2go**. There is a server and a client. Clients exist for the 3 main desktops.  All connections go over ssh tunnels automatically, so it is secure. Connections from different continents works.  Plus the performance is 2-3x faster than rdp or vnc solutions.  x2go doesn't support every DE or WM out there out of the box.  Unity is NOT supported, so using xfce or lxde are highly recommended.  All the features of ssh work, so if the client has provided ssh-keys to the server, that will be used for authentication.  People who switch from VNC to x2go say "it is like night and day."  Instructions are here: [http://wiki.x2go.org/doku.php/doc:installation:x2goserver](http://wiki.x2go.org/doku.php/doc:installation:x2goserver)

---

