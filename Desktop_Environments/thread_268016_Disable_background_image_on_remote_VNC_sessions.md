---
title: "Disable background image on remote VNC sessions?"
date: 2006-09-29
forum: Desktop Environments
---

### Post by zurih on 2006-09-29
Hi

I'm trying to configure Xvnc so when I connect remotely, the background image will be disabled. This is while as the same username which I login with, still has its background image on the local machine.

Is this possible?

This is my currunt /etc/xinetd.d/Xvnc file:
```

service Xvnc
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/Xvnc
        server_args = -inetd :1 -query localhost -geometry 1280x1024 -depth 16 -once -fp /usr/share/X11/fonts/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd
        port = 5901
}

```

Thanks!

---

