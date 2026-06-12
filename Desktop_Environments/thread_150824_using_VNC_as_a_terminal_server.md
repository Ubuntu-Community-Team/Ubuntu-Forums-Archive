---
title: "using VNC as a terminal server"
date: 2006-03-26
forum: Desktop Environments
---

### Post by countryboy on 2006-03-26
Hi all

I have looked through all the archives but I haven't found anything about using VNC as a Terminal Server type set up on uBuntu.

I have a Red Hat box that allows multiple VNC sessions to be run at the same time, but when I use the same configuration it does not seem to work on uBuntu.

Getting VNC to work on display:0 is no problem, but I want multiple sessions at once. I know it places a heavy demand on resources, but this is the way it has to be done. 

Unfortunately the HOW-TO doesn't quite give me what I need.

Does anybody know how to get uBuntu to run properly as a Terminal Server?

Thanks

---

### Post by countryboy on 2006-03-26
This is what my /etc/xinetd.d/vnc file looks like

```
service vnc-login
{
disable = no
socket_type = stream
protocol = tcp
wait = no
user = administrator
server = /usr/bin/Xvnc
server_args = -inetd :42 -once -query localhost -geometry 1000x700 -depth 16 -fp /usr/share/X11/fonts/misc -SecurityTypes=None -passwordfile=0 -auth /var/lib/gdm/:0.Xauth
type = UNLISTED
port = 5942
}

```

all I get is a grey screen, plus no-one else can start another session.

On my Red Hat boxes which allow multiple VNC sessions, the /etc/xinetd.d/vnc file looks like this:

```

service vnc-login
{
socket_type = stream
protocol = tcp
wait = no
user = administrator
server = /usr/bin/Xvnc
server_args = -inetd :42 -once -query localhost -geometry 1000x700 -depth 16 -fp unix/:7100 -securitytypes none
type = UNLISTED
port = 5942
}

```

---

### Post by countryboy on 2006-03-29
Forget it. I just used FreeNx instead.

---

