---
title: "Launch REMOTE DESKTOP from command line?"
date: 2005-05-30
forum: Desktop Environments
---

### Post by ubuntuzen on 2005-05-30
Hi all,

it is possible to run Remote Desktop from a command line,
accessing all the options (parameters) ?

I like to log-on to SSH (from Win machine) and Launch the Remote Desktop
to have some GUI features available to the Win box.

I'm trying VCN4SERVER but don't know how to run it ...

Thanks all,
Valter

---

### Post by cwaldbieser on 2005-05-30
If you want to access your Ubuntu GUI from a Windows client, I don't think that running remote desktop on the Ubuntu machine will work.  Remote desktop is a client program-- the machine whose desktop you want to see needs to be running a terminal server for it to work.

VNC is probably the way to go.  It is pretty simple to set up, and it is available as client and server on many platforms.  Here are some links that might help:

[http://www.benjamin.weiss.name/putty-tunnel.html](http://www.benjamin.weiss.name/putty-tunnel.html)
[http://www.uk.research.att.com/archive/vnc/sshvnc.html](http://www.uk.research.att.com/archive/vnc/sshvnc.html)
[http://www.vanemery.com/Linux/VNC/vnc-over-ssh.html](http://www.vanemery.com/Linux/VNC/vnc-over-ssh.html)

---

### Post by testingubuntu on 2005-05-30
tsclient  willl launch  terminal server client 

you then can choose the protocol you need . rdp vnc etc...

---

