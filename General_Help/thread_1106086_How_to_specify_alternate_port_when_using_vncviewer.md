---
title: "How to specify alternate port when using vncviewer and -via"
date: 2009-03-25
forum: General Help
---

### Post by InkyDinky on 2009-03-25
I'm trying to vnc using the -via command to tunnel via ssh.  The ssh on this machine listens on a port other than the standard ssh port of 22.  How do I specify this alternate port? 
Currently this is what command I'm attempting:
```

vncviewer -via bob@foo.bar.com:511 localhost:0
ssh: Could not resolve hostname foo.bar.com:511: Name or service not known
vncviewer: Tunneling command failed: /usr/bin/ssh -f -L 5599:localhost:5900 bob@foo.bar.com:511 sleep 20.

vncviewer -via bob@foo.bar.com -p 511 localhost:0
ssh: connect to host foo.bar.com port 22: Connection refused
vncviewer: Tunneling command failed: /usr/bin/ssh -f -L 5599:localhost:5900 bob@foo.bar.com sleep 20.

```

Thanks
Nick

---

### Post by InkyDinky on 2009-03-25
So it appears that I need to change something in the environment variable VNC_VIA_CMD.  Hopefully I'm getting somewhere.

---

### Post by wajjs on 2009-04-08
I was looking for this aswell.
The only thing i found was:

vncviewer -via "user@host -p port" localhost:0

found it in:
[http://ubuntu-tutorials.com/2007/06/12/vnc-over-ssh-securing-the-remote-desktop/](http://ubuntu-tutorials.com/2007/06/12/vnc-over-ssh-securing-the-remote-desktop/)

but that did not work for me :(
I have a vncserver on pot 5901

vncviewer -via "wajs@localhost -p xxxx"  localhost:1
Error:
main:        unable to connect to host: Connection refused (111)

---

### Post by wajjs on 2009-04-08
I checked out:
[http://www.realvnc.com/products/free/4.1/man/vncviewer.html](http://www.realvnc.com/products/free/4.1/man/vncviewer.html)
They have removed the -via command from it ???
So it's just the viewer thats useless.

Found a better better viewer called xtightvncviewer
It is in the ubuntu repo:
[http://packages.ubuntu.com/search?keywords=xtightvncviewer](http://packages.ubuntu.com/search?keywords=xtightvncviewer)

xtightvncviewer -via "wajs@localhost -p xxxx" localhost:1

worked!

oh and if anyone wounder why I would want to tunnel to my own
computer. that was just for testing :)

---

### Post by InkyDinky on 2009-04-13
Awesome! using that syntax with the quotes worked for me.
I didn't have to dl xtightvncviewer either.
vncviewer -via "user@host.com -p XXXX" localhost:0 
is what I used and it worked like a charm.

---

### Post by lance bermudez on 2010-03-06
xtightvncviewer -via "pete@192.168.2.103" localhost:0

works for the linux but i want to be able to set the -compresslevel 9 -x11cursor tags. how do i do that?

---

### Post by lance bermudez on 2010-03-06
xtightvncviewer -via "pete@192.168.2.103 -p 22" -compresslevel 9 -x11cursor localhost:0
the above works for linux i have another computer that i need to connect to from my linux box it is a windows xp computer with tightvnc on it set to accept port 22 how do i use the -via to connect to that computer also

---

### Post by Chris_82 on 2011-11-20
This has been working nicely for me. The -C adds compression to the ssh traffic and improves the speed a lot, especially on not too fast remote networks:

```
xtightvncviewer -bgr233 -compresslevel 4 -quality 3 -encodings tight -via "-C via_user@via_host -p via_port" vnc_host
```

---

