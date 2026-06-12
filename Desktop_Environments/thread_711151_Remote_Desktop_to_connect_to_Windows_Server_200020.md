---
title: "Remote Desktop to connect to Windows Server 2000/2003 only 15 days left"
date: 2008-02-29
forum: Desktop Environments
---

### Post by RikardSvenningsen on 2008-02-29
Hi
I have bee using tsclient for some years now, and from time to time searched for a solution on some Windows License problem.
After a while (like 60 days maybe) it starts tell me that I only have some days back to use this connection. If I rename my computer to a new name I got a new period of time to use the connection.
I know from MAC that they have the same problem but they can delete a file and then get a new period of time.
Any one know howto remove this problem.

---

### Post by kevinatkins on 2008-02-29
Hi,

I'd be inclined to install a VNC server on your Windows 2003 and use vncviewer on Linux to establish a remote connection instead. You won't have any licensing issues then!

That's what I've got set up on corporate machines that I maintain remotely.

---

### Post by Fire_Chief on 2008-02-29
Is your Windows Server running Terminal Services in Remote Administration mode or in Application mode (aka full terminal server system)? If it is in Remote Admin mode you should not ever see license notifications but are limited to two simultaneous RDP sessions to the server (not counting a console connection).

---

### Post by RikardSvenningsen on 2008-03-01
Regarding VNC:
I use VNC inside the local LAN, I don't fell the security is strong enough to use it outside and it's not as fast as the Terminal server, The screen update works better on the terminal server. (Not that I love MS for it's innovation :) )
About the running mode:
I got both, one is running as Administrator mode another is running user mode, it's on windows 2000, I also got one Windows 2003 running in administrator mode, all with the same problem. But as I have told before on MAC (Appel) you just remove a file (not remember what file..) and you are up and running for a new period.

---

### Post by kevinatkins on 2008-03-01
Hi,

Yes VNC security would be too weak to run across a WAN, but for that I use a VPN tunnel.

---

### Post by RikardSvenningsen on 2008-03-23
As I can see there seems to be no solution on this topic.

---

