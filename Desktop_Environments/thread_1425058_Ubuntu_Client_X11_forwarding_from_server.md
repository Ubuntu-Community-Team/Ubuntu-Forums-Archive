---
title: "Ubuntu Client X11 forwarding from server"
date: 2010-03-08
forum: Desktop Environments
---

### Post by cbo0485 on 2010-03-08
Okay, so here's the situation.  I have an Ubuntu 9.10 desktop here at my work, and I'm trying to use the terminal(gnome-terminal), and then using SSH to SSH into a remote server(non-gui server).  Now, this server does have x11 Forwarding turned on, b/c I can do all of this from a Windows Laptop using Putty and Cygwin.

So anyway, I just need to be able to ssh into the remote server, and then run a program which has a GUI, and obviously get the window.  

Here is some output from when I used ssh -X -v remote_server

```

[remote_server]:/home/user>xclock
debug1: client_input_channel_open: ctype x11 rchan 3 win 65536 max 16384
debug1: client_request_x11: request from 127.0.0.1 52629
debug1: channel 1: new [x11]
debug1: confirm x11
X11 connection rejected because of wrong authentication.
debug1: channel 1: free: x11, nchannels 2
X connection to localhost:11.0 broken (explicit kill or server shutdown).
[remote_server]:/home/user>echo $DISPLAy
localhost:11.0

```

---

### Post by cbo0485 on 2010-03-09
anyone have any ideas?

---

### Post by cjhabs on 2010-03-09
On your desktop, what are the results from "xhost" ? Are X apps allowed to display to your desktop?
You could try "xhost +" just for testing.

---

### Post by cbo0485 on 2010-03-09
> **cjhabs said:**
> On your desktop, what are the results from "xhost" ? Are X apps allowed to display to your desktop?
You could try "xhost +" just for testing.

I did that and it worked for my user.  But I need to be able to run a program as another user, I have to su - svcacct, and then run the program.  I think that's what is causing the issues.

---

### Post by cjhabs on 2010-03-09
What error are you getting?

---

### Post by yjarbou on 2010-04-11
you need to enable X11 forwarding when you connect through SSH:  % ssh -X server_ip

---

