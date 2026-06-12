---
title: "X2Go on Ubuntu 14.04 Headless"
date: 2014-11-06
forum: Desktop Environments
---

### Post by ben-magee on 2014-11-06
Hi,

I've been trying to get X2Go working on Ubuntu 14.04 server (headless).

I originally had it working on a fresh install of 12.04, did the distribution upgrade to 14.04 and suddenly it's stopped working. The x2goserver starts fine on the server, however my client just won't connect. Here's what is displayed in the x2go client (on windows):

```

  NXPROXY - Version 3.5.0

 

 Copyright (C) 2001, 2010 NoMachine.

 See http://www.nomachine.com/ for more information.

 

 Info: Proxy running in client mode with pid '6516'.

 Session: Starting session at 'Thu Nov  6 14:39:34 2014'.

 Info: Connecting to remote host 'localhost:31001'.

 Info: Connection to remote proxy 'localhost:31001' established.

 Connection timeout, aborting


```

At that point it stops working. The desktop never opens.

I've tried reinstalling both the server and client with no luck. I can SSH into the machine fine.

Any help is appreciated!

---

### Post by TheFu on 2014-11-06
Check the ssh logs on the server as x2go connects.
Also check the server-side syslog.

Have you tried different sessions or running an xterm directly?

---

