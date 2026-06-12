---
title: "TightVNC b/w Ubuntu and Winders"
date: 2006-05-22
forum: Desktop Environments
---

### Post by travishume on 2006-05-22
I installed TightVNC v1.2.9 on a Windows XP machine and put it into listen mode.  I have xtightvncviewer-1.2.9-8ubuntu2 installed on my Ubuntu machine.

When I try and connect Ubuntu to Windows XP if fails with a protocol version mismatch error:

```
VNC server supports protocol version 3.6 (viewer 3.3)
```

Seems strange that the same version (1.2.9) is talking a different protocol.
Suggestions?

---

### Post by louis_nichols on 2006-05-22
try using another vncviewer on ubuntu. realvnc or something.

it's a standard, so you don't have to use the same app both ways.

---

### Post by travishume on 2006-05-22
I tried realvnc with the same result.

```

VNC viewer version 3.3.7 - built Feb 20 2006 12:04:05
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
VNC server supports protocol version 3.6 (viewer 3.3)
VNC connection failed: The VMRC connection could not be established because protocol version 3.6 or later is required.

```

---

### Post by phurley on 2006-11-29
I am getting the same error, did you ever get a resolution on this issue?

Thanks
pth

---

### Post by Sanek on 2008-01-18
I had same issue:

sasha@rastseluev_nb:~$ krdc
current depth: 0
VNC server supports protocol version 3.6 (viewer 3.3)
VNC connection failed: The VMRC connection could not be established because protocol version 3.6 or later is required.
ShmCleanup called
current depth: 0
Color depth: 8
Tried to read some related posts, but no result.
Then i've tried this:

sasha@rastseluev_nb:~$ rdesktop 10.11.12.13
Autoselected keyboard map en-us
disconnect: No license server available.  
(I knew this, from windows it was accessible only through mstsc /console)
Read man rdesktop & found option -0 !!!
Finally i've got it working with:
rdesktop -0 10.11.12.13

---

### Post by branbuntu on 2008-06-18
Hello,

I use UltraVNC 1.02 on Windows XP and Server 2000
I use the Terminal Server Client in Ubuntu 8.04
I installed the common vnc components first, so that the option is no longer greyed out.

apt-get install vnc-common xtightvncviewer

I configured the authentication settings on my XP UltraVNC so that:

Uncheck "Require MS Logon (User/Pass/Domain)"
Specify a VNC Password

By following the above step, I no longer received authentication errors when connecting via Ubuntu.

Brandon.

---

