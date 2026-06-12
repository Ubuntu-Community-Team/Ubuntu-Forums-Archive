---
title: "x2go session terminates immediatly"
date: 2015-07-02
forum: Desktop Environments
---

### Post by petert2 on 2015-07-02
Hi,

I am trying to replace my home Windows server with Ubuntu 14.04 LTS, i am setting it up on a VMware virtual machine until i have it mostly configured to avoid disrupting media playback, but i am having problems getting any kind of remote desktop going.

I am currently trying to use x2go, but whenever i connect, it seems like its working and then it immediatly terminates.

The only "session.log" i can find is in home/<username>/.x2go/C-pt-50-1435810369_stDKDE_dp32/. I have included the content below.

However i can see that when i try to connect, that another folder is created (C-pt-50-...-stDUNITY_dp32), but for some reason it is deleted again almost immediatly. I managed to grab its session.log though, and have included it below after the first one.

I have tried Unity, Gnome and KDE settings in the x2go client, but always get the same behavior. The only thing that worked was connecting to "local desktop" of an existing session, but i found the performance fairly horrible. Especially considering that i am connecting to a local VM (running i7 5820k@4ghz (6 cores) and 32gb DDR4 so plenty of resources available). Its a bit slower than what i get with RDP to my windows workstation at work (ie. over a 15/2 ADSL connection). The machine hosting the VM which i am connecting from is running Win 8.1 x64.

```

running as X2Go Agent

NXAGENT - Version 3.5.0

Copyright (C) 2001, 2011 NoMachine.
See http://www.nomachine.com/ for more information.

Info: Agent running with pid '43436'.
Session: Starting session at 'Wed Jul  1 21:12:49 2015'.
Info: Proxy running in server mode with pid '43436'.
Info: Waiting for connection from 'localhost' on port '30001'.
Info: Accepted connection from '127.0.0.1'.
Info: Connection with remote proxy completed.
Info: Using LAN link parameters 1536/24/1/0.
Info: Using agent parameters 5000/0/50/0/0.
Info: Using pack method '16m-jpeg-9' with session 'unix-kde-depth_32'.
Info: Not using NX delta compression.
Info: Not using ZLIB data compression.
Info: Not using ZLIB stream compression.
Info: Not using a persistent cache.
Info: Listening to X11 connections on display ':50'.
Info: Established X client connection.
Info: Using shared memory parameters 1/1/0/0K.
Info: Using alpha channel in render extension.
Info: Not using local device configuration changes.
keyboard file created
Session: Session started at 'Wed Jul  1 21:12:53 2015'.
Session: Terminating session at 'Wed Jul  1 21:12:54 2015'.
Info: Waiting the cleanup timeout to complete.
Session: Session terminated at 'Wed Jul  1 21:12:54 2015'.

```

```

running as X2Go Agent

NXAGENT - Version 3.5.0

Copyright (C) 2001, 2011 NoMachine.
See http://www.nomachine.com/ for more information.

Info: Agent running with pid '93195'.
Session: Starting session at 'Thu Jul  2 12:03:22 2015'.
Info: Proxy running in server mode with pid '93195'.
Info: Waiting for connection from 'localhost' on port '30001'.
Info: Accepted connection from '127.0.0.1'.
Info: Connection with remote proxy completed.
Info: Using ADSL link parameters 512/24/1/0.
Info: Using agent parameters 5000/10/50/0/0.
Info: Using cache parameters 4/4096KB/8192KB/8192KB.
Info: Using pack method '16m-jpeg-9' with session 'unix-kde-depth_32'.
Info: Using ZLIB data compression 1/1/32.
Info: Using ZLIB stream compression 4/4.
Info: No suitable cache file found.
Info: Listening to X11 connections on display ':50'.
Info: Established X client connection.
Info: Using shared memory parameters 1/1/0/0K.
Info: Using alpha channel in render extension.
Info: Not using local device configuration changes.
keyboard file created
Session: Session started at 'Thu Jul  2 12:03:23 2015'.
Session: Terminating session at 'Thu Jul  2 12:03:25 2015'.
Info: Waiting the cleanup timeout to complete.
Session: Session terminated at 'Thu Jul  2 12:03:25 2015'.

```

---

### Post by TheFu on 2015-07-02
Unity and gnome3 are NOT supported by x2go.  There are specifically supported DEs - pick one of those.  I don't recall the exact supported list - but xfce4 and lxde ARE supported.

That is just 1 possibility.  Others are that ssh is being blocked - so - test with just ssh from a shell (or cough putty if you must). Does that work?

Disable remote audio and remote printing support while troubleshooting this.  

And my final tip is for Windows users - there are font packages at the x2go website.  I decided it wasn't worth my time to figure out which fonts I needed, so I grabbed the 'get-everything' package and carefully followed the instructions.

Hope these ideas are helpful.

---

### Post by petert2 on 2015-07-03
The x2go client has a specific option for "Unity", isnt that a bit weird if it isn´t supported? Also, i did manage to login to an existing X-window session as described above, so i dont think this or ssh is a problem (or perhaps the reason it looked a bit grainy and was slow was that it wasn´t specifically supported?).

I already disabled remote audo and printing.

I will try the font packages.

When x2go is working, does it still show significant lag and compression artifacts over LAN?

---

### Post by petert2 on 2015-07-03
Ah, this explains the compatiblity issues :

[http://wiki.x2go.org/doku.php/doc:de-compat](http://wiki.x2go.org/doku.php/doc:de-compat)

---

### Post by petert2 on 2015-07-04
After quite a few false starts where nothing worked, i ended up with Ubuntu Server + MATE (both LXDE and Xfce4 are horribly atrocities if you as me :) Now X2Go is working great, and seems really snappy.

---

### Post by TheFu on 2015-07-04
> **petert2 said:**
> After quite a few false starts where nothing worked, i ended up with Ubuntu Server + MATE (both LXDE and Xfce4 are horribly atrocities if you as me :) Now X2Go is working great, and seems really snappy.

So - Solved?

BTW, you can get more performance by dropping any DE and going with a pure WM instead.  Openbox and fvwm-crystal work.

---

### Post by petert2 on 2015-07-06
> **TheFu said:**
> So - Solved?

BTW, you can get more performance by dropping any DE and going with a pure WM instead.  Openbox and fvwm-crystal work.

Yes, its solved, should i mark it solved somehow?

I don´t need more performance, MATE is running super snappy and i like the interface, the machine is an old i3 530 w/ 8gb RAM. It ran slow as hell with Windows server though.

---

