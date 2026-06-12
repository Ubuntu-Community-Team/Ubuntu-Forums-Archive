---
title: "xinetd won't allow vncserver to start"
date: 2006-09-16
forum: Desktop Environments
---

### Post by paperdiesel on 2006-09-16
Whenever I try to run a vncserver on my kubuntu 6.06 box, I get this message:

```

ti@ti-kubuntu:~$ xvncviewer localhost:6
VNC viewer version 3.3.7 - built Feb 20 2006 12:04:05
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See http://www.realvnc.com for information on VNC.
ReadFromRFBServer: rdr::SystemException: read: Connection reset by peer (104)
ti@ti-kubuntu:~$                                                              

```

I also tried setting it up on :1 (port 5901), but that gave me the same result.  When I just run vncserver without doing it through xinetd, it works perfectly.  What am I doing wrong?  I know xinetd is listening:

```

ti@ti-kubuntu:~$ sudo netstat -tap | grep xinetd
tcp        0      0 *:5906                  *:*                     LISTEN     5497/xinetd
ti@ti-kubuntu:~$               

```

Anyone?

---

### Post by kokild on 2008-03-15
in /etc/xinetd.d/Xvnc, add the following to the server_args:
-extension XFIXES.

This seems to solve the problem.

After that restart you xinetd, (the usual way):
sudo /etc/init.d/xinetd stop
sudo /etc/init.d/xinetd start

Now when you connect to :1, you should be able to see the login screen.

---

