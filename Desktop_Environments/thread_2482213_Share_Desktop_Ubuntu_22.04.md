---
title: "Share Desktop Ubuntu 22.04"
date: 2022-12-24
forum: Desktop Environments
---

### Post by securitydad on 2022-12-24
I am trying to connect Desktop Sharing for my Ubuntu box to Windows.  I have followed the guide - [https://help.ubuntu.com/stable/ubuntu-help/sharing-desktop.html](https://help.ubuntu.com/stable/ubuntu-help/sharing-desktop.html) and when I attempt to use the mstsc (Remote Desktop tool) for Windows 10, I get a protocol error in connection, the window closes.

Has anyone gotten this to work?

---

### Post by ActionParsnip on 2022-12-26
What are you wanting to do on the remote system that needs the full desktop session? There may be a sleeker solution to what you want to do

---

### Post by securitydad on 2023-01-15
I want to create a Teamviewer replacement.

---

### Post by ActionParsnip on 2023-01-15
What activities will you be doing once connected? This is my question

---

### Post by TheFu on 2023-01-15
> **securitydad said:**
> I want to create a Teamviewer replacement.

There are many solutions possible.

It is unclear to me if you want to connect from Linux to Windows
or
if you want to connect from Windows -to- Linux.

In general, ssh is used to connect Unix-like OSes.

Text: ssh user@server

Remote X11 with X11forwarding: ssh -X user@remote-server command-on-remote-system

Remote Desktop using NX-based x2go: there's a client and server.  Install the ssh and x2go server on the Linux system. Then install the x2go-client on the client.  I think MS-Windows clients need some fonts installed too.  Setup ssh in the text connection way to work first.

'user' is the username on the remote system.
'server' is the DNS or IP of the remote system.  It can be running any version of Unix/Linux. just ensure that ssh is installed.
Remote X11 requires the local system runs an X/Server.  MS-Windows doesn't include this, but free versions, xming, are available.

A full remote desktop has far too much overhead for most uses.  Favor using ssh with or without X11 forwarding.  This is what Unix admins have used to manage systems around the world for decades.

---

