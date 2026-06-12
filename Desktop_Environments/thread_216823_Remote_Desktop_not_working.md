---
title: "Remote Desktop not working"
date: 2006-07-16
forum: Desktop Environments
---

### Post by Webspot on 2006-07-16
I go to System -> Preferences -> Remote Desktop

Set up the vncserver to ask for a password. Enter the password. Click close.

Start up a terminal. Type vncviewer localhost:0. Get this output

```
VNC viewer version 3.3.7 - built Feb 20 2006 12:04:05
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See http://www.realvnc.com for information on VNC.
vncviewer: ConnectToTcpAddr: connect: Connection refused
Unable to connect to VNC server
```

Any idea what is wrong?

---

### Post by Webspot on 2006-07-16
I just restarted the computer and now I get this message when I try it:

```
VNC viewer version 3.3.7 - built Feb 20 2006 12:04:05
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See http://www.realvnc.com for information on VNC.
VNC server supports protocol version 3.7 (viewer 3.3)
ReadFromRFBServer: rdr::EndOfStream

```

---

### Post by rockfloyd on 2006-07-17
man i've been trying to get this to work too.. mine doesn't even do anything at all when i type in the correct commands.

---

### Post by 0NeX0 on 2006-07-18
you need to make sure you are using the right ports like if you ssh into it and start the vnc server from thier you need to use vncviwer localhost:1 becuse screen 0 is on the desktop and 1 is the virtual one. let me know if you need any more assitance, also you need to make sure you have vncserver and vncclient installed here is a link to help you further

[http://abowman.com/2006/07/02/secure-remote-access-with-vnc-and-ssh/](http://abowman.com/2006/07/02/secure-remote-access-with-vnc-and-ssh/)

---

### Post by scxtt on 2006-07-18
it would make much more sense to connect to your box from another box that's not your own (why connect to localhost:0 when you're sitting right on front of it?)

vino, what you're using, uses port 5901 - "normal" VNC uses port 5900 - so keep that in mind if you've got a firewall running ...

---

### Post by 0NeX0 on 2006-07-19
yes ur are right i was not all here last night when i replied to that msg please forgive. and thanks for clearing that up

---

