---
title: "gdmXnest won't start"
date: 2007-12-10
forum: Desktop Environments
---

### Post by tengil on 2007-12-10
Hi. I'm struggling to get gdmthemetester to work on Gutsy and have narrowed it down to gdmXnest (which works fine on my other laptop running Feisty).

Here's what happens:

```

tengil@tavla:~$ gdmXnest
DISPLAY=:20

Fatal server error:
Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again.

tengil@tavla:~$ sudo rm /tmp/.X0-lock
[sudo] password for tengil:
tengil@tavla:~$ 
tengil@tavla:~$ gdmXnest
DISPLAY=:20
_XSERVTransSocketUNIXCreateListener: ...SocketCreateListener() failed
_XSERVTransMakeAllCOTSServerListeners: server already running

Fatal server error:
Cannot establish any listening sockets - Make sure an X server isn't already running

tengil@tavla:~$ uname -a
Linux tavla 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

```

I'm running xgl for compiz under ati/fglrx but this happens whether xgl is enabled or disabled. Are there any logs I could check? Any feedback would be helpful...

---

