---
title: "Unable to Connect to VNC server"
date: 2009-03-08
forum: General Help
---

### Post by tiger.woods on 2009-03-08
I was able to login and use VNC from my Windows machine, I rebooted my Ubuntu box and now I can't connect. Does the VNC server need to be restarted each time I reboot my box?

Any help would be appreciated.

Thanks,

---

### Post by tiger.woods on 2009-03-08
This is a headless machine and now I see that vino isn't listening on 5900.

Why didn't the vncserver start after a reboot?


> $$ netstat -ln -A inet
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 127.0.0.1:13666         0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN
udp        0      0 192.168.1.111:137       0.0.0.0:*
udp        0      0 0.0.0.0:137             0.0.0.0:*
udp        0      0 192.168.1.111:138       0.0.0.0:*
udp        0      0 0.0.0.0:138             0.0.0.0:*
udp        0      0 0.0.0.0:49864           0.0.0.0:*
udp        0      0 0.0.0.0:5353            0.0.0.0:*


---

### Post by tiger.woods on 2009-03-08
I've solved the problem on this machine it had a hard lock and wouldn't boot past the POST screen, I had to unplug the power supply and all seems to be well..

Sorry for the noise.

TW,

---

