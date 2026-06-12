---
title: "Xvnc4 started from xinetd only displays empty gray X screen"
date: 2011-03-20
forum: Desktop Environments
---

### Post by scott8035 on 2011-03-20
Hi. I'm attempting to setup an Ubuntu 10.10 box so that anyone can connect to port 5900 and be greeted by the gdm login manager. To do so, I added a vnc entry in /etc/services and I am starting Xvnc4 using this xinetd config file:

```

service vnc
{
  protocol = tcp
  socket_type = stream
  wait = no
  user = nobody
  server = /usr/bin/Xvnc
  server_args = -geometry 1000x700 -depth 24 -broadcast -inetd -once -securitytypes None
}

```

This kind of works...I can start multiple sessions all to port 5900, and I get an X screen. The problem is that I only get an empty, gray X screen with no applications started.

I know when you run vncserver from the command line it will look to your ~/.vnc/ directory for your passwd and xstartup files, and I think what I want to do is put "gnome-session" into the xstart file. However, which xstartup file? The running user is "nobody" who obviously doesn't have a ~/.vnc/ directory. I tried a /root/.vnc/xstartup file and a ~scott/.vnc/xstartup file and it doesn't look like they were even read.

I changed the xinetd vnc service so that it would "strace" Xvnc4. I looked thru all the "open" lines and didn't get a clue as to what file it was trying to read for xstart.

Can anyone help? I just want a terminal server where the user is presented with a gdm login screen.

---

### Post by scott8035 on 2011-03-24
I finally gave up on this, started fresh from a snapshot of my system, and installed xrdp and vnc4server. Worked right out of the box. Very frustrating. I will be trying VNC again when 11.04 comes out.

---

### Post by nmw01223 on 2011-04-10
I suspect it's the geometry parameter. I've done pretty much the same thing and providing I leave -geometry out - defaults to 1024x768 - it works, put anything else in, and I get the same as you - no login prompt.

No idea why - Linux newbie - looking for an answer ....

---

