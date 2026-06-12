---
title: "TightVNC woes!"
date: 2006-09-04
forum: Desktop Environments
---

### Post by Copps on 2006-09-04
Hope someone can help.

I'm trying to set up remote desktop access to my Ubuntu machine, both from the other (Windows) machine on the same local network, and from my PC at work (external network).

I've set up port forwarding on my router for port 5900 to the internal IP of my computer, and followed the instructions at [http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_connect_into_remote_Ubuntu_desktop_via_Windows_machine](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_connect_into_remote_Ubuntu_desktop_via_Windows_machine) for configuring remote desktop options.

I've downloaded TightVNC viewer to both Windows boxes, but when I try to run it to connect to Ubuntu by IP address, I receive a "Failed to connect to server" error message.

I expected to see something useful, somehere, in /var/log on the Ubuntu box, but there is nothing to help me. I don't run a firewall on Ubuntu yet. I've tried disabling the firewalls on the PCs I'm connecting from, to no avail. If I boot the Ubuntu box into it's Windows partition, I can connect Windows to Windows via RDP, so there's no issue with the machines I am trying to connect from recognising the IP address of the target machine.

Anyone have any other pointers please?

---

### Post by sefs on 2006-09-04
You may be missing something simple like enabling xdmcp. ect.

Also take a look at these guides...

[http://ubuntuforums.org/showthread.php?t=191564&highlight=vnc+resumable+sessions](http://ubuntuforums.org/showthread.php?t=191564&highlight=vnc+resumable+sessions)

and 

[http://ubuntuforums.org/showthread.php?t=122402&highlight=vnc+resumable+sessions](http://ubuntuforums.org/showthread.php?t=122402&highlight=vnc+resumable+sessions)


pay spectial attention to when they tell you create a file that has ...

```
service Xvnc { type = UNLISTED disable = no socket_type = stream protocol = tcp wait = yes user = root server = /usr/bin/Xvnc server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/X11/fonts/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd port = 5901 }
```

That above is not suppose to be on one line in the file, but on multiple lines.... one of the links above explains it.

---

