---
title: "Remote Desktop (vncviewer) generates extreme amount of traffic"
date: 2006-07-07
forum: Desktop Environments
---

### Post by fuxoft on 2006-07-07
When I connect to my second box using using vncviewer (both of them are running the latest Dapper), it generates LOTS of traffic: I see constant throughput of 500kB/s on eth0, even if the remote screen is completely static - this considerably slows down all other traffic on my home network (5 computers in total). I tried running vncviewer with option "-noauto" which helps a little, the traffic then is "only" around 200kB/s (also constant, regardless of what is happening).

tcpdump shows lots and lots of these:

```
11266327 15908367> 14:31:11.477002 IP frantisek.fx.39904 > 10.9.8.99.5900: P 168421:168431(10) ack 4048826 win 32674 <:nop,nop,timestamp
15908368 11266327> 14:31:11.477569 IP 10.9.8.99.5900 > frantisek.fx.39904: P 4048826:4049062(236) ack 168431 win 1448 <:nop,nop,timestamp
11266327 15908368> 14:31:11.478197 IP 10.9.8.99.5900 > frantisek.fx.39904: P 4049062:4049298(236) ack 168441 win 1448 <:nop,nop,timestamp
```

---

### Post by mlind on 2006-07-07
Have you tried if using alternative VNC server like tightvnc or FreeNX reduce the traffic?

---

### Post by fuxoft on 2006-07-08
I'm afraid that I'll mess up the default vncserver by installing another one. Anyway, I need to connect to several "vanilla" Ubuntu installations in this way. Installing vnc servers on all of them should really be the last resort.

---

### Post by mlind on 2006-07-08
> **fuxoft said:**
> I'm afraid that I'll mess up the default vncserver by installing another one. Anyway, I need to connect to several "vanilla" Ubuntu installations in this way. Installing vnc servers on all of them should really be the last resort.

I don't think you notice anything else than faster performance, if you replace  default vnc server with tightvnc. VNC is for remote desktop usage. If you don't want to use it, there's always alternative ways like tunneling X connetions through ssh. 

If you don't need X server, you can just setup simple networking. No need for VNC.

---

