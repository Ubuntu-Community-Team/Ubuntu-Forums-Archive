---
title: "Can't open display - X tcp connection issue"
date: 2005-10-19
forum: Desktop Environments
---

### Post by tepegoz on 2005-10-19
Hi all,
I am using solaris machines, and transfer gui to ubuntu box. 
I do "xhost +machine_name" on the ubuntu box, and then connect to the solaris, and do "setenv DISPLAY ip:0". But solaris cannot open X connection.
The problem is this: Xwindows on ubuntu box does not listen tcp packets.
In hoary, I had changed the property of listen tcp connections from gnome_session properties (as I remember). But it is not there in breezy. Anyone knows where that option gone?

I also checked allow_tcp_connections in gconf, but it didn't not work.

Thanks in advance.

---

### Post by munitras on 2005-10-19
on CMD line

```
sudo vi /etc/X11/xinit/xserverrc
```

change 

```
exec /usr/bin/X11/X -dpi 100 -nolisten tcp
```

to 

```
exec /usr/bin/X11/X -dpi 100
```

else in GUI

System -> Administration -> Login Screen Setup

go to the "Security" Tab

make sure the "Deny TCP connections to Xserver..." option is /not/ checked.

I think you will have to re-start X

---

### Post by tepegoz on 2005-10-20
Hi
System->Administration->Login Screen Setup works.
Thanks a lot.

---

