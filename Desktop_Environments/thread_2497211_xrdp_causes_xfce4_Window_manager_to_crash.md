---
title: "xrdp causes xfce4 Window manager to crash"
date: 2024-04-27
forum: Desktop Environments
---

### Post by ski-brimson on 2024-04-27
When I start xfce4 normally from the console or with startxfce4 using ssh and X11 tunneling, xfce4 seems to work fine.  When I use xrdp/rdp, it seems to crash.

I see the start/logout bar come up, but the application icons do not appear before it crashes.

```
[20240426-23:42:30] [INFO ] Session in progress on display 11, waiting until the window manager (pid 27072) exits to end the session
[20240426-23:42:37] [WARN ] Window manager (pid 27072, display 11) exited with non-zero exit code 255 and signal 11. This could indicate a window manager config problem
[20240426-23:42:37] [WARN ] Window manager (pid 27072, display 11) exited quickly (7 secs). This could indicate a window manager config problem
[20240426-23:42:37] [INFO ] Calling auth_stop_session and auth_end from pid 27071
[20240426-23:42:37] [INFO ] Terminating X server (pid 27073) on display 11
[20240426-23:42:37] [INFO ] Terminating the xrdp channel server (pid 27078) on display 11
[20240426-23:42:37] [INFO ] X server on display 11 (pid 27073) returned exit code 255 and signal number 6
[20240426-23:42:37] [INFO ] xrdp channel server for display 11 (pid 27078) exit code 0 and signal number 0
[20240426-23:42:37] [INFO ] cleanup_sockets:
[20240426-23:42:37] [INFO ] ++ terminated session:  username klugja, display :11.0, session_pid 27071, ip ::ffff:192.168.0.58:34422 - socket: 12
```


This is startwm.sh at the tail:

```
if test -r /etc/profile; then
    . /etc/profile
fi

# test -x /etc/X11/Xsession && exec /etc/X11/Xsession
exec startxfce4 >/tmp/startxfce4.txt 2>&1

```

This is Ubuntu 22.04
xrdp:
0.9.17-2ubuntu2
xfwm4:
4.16.1-1 

Since xfmw4 is running when things are working, I assume xrdp is crashing xfmw4?

I am attaching the output of startxfce4.txt, because it is full of errors. I have no idea which errors if any explain the memory fault error.

---

### Post by ski-brimson on 2024-04-29
I installed fluxbox.  At the end of /etc/xrdp/xrdp.conf:
```

# test -x /etc/X11/Xsession && exec /etc/X11/Xsession
exec startfluxbox
```
Now xrdp works.  I only have to configure fluxbox now.

---

### Post by ActionParsnip on 2024-04-29
What are you doing on the remote system that needs the full desktop session? There may be a sleeker solution to what you want to achieve

---

