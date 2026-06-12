---
title: "Vnc client"
date: 2006-01-12
forum: Desktop Environments
---

### Post by evendramin on 2006-01-12
I am using Ubuntu 5.10 and I need to connect with a workstation WinXP running RealVNC server. 

Anyone knows how to do this ? 

I am trying the xrealvncviewer unsucessfully :confused: .

Thanks...

---

### Post by ahessling on 2006-01-12
On my machine I have under GNOME's Applications -> Internet a link to a Terminal Server Client. I never tried it but it looks like a nice frontend to VNC and it supports AFAIK the RealVNC protocol.
Give it a try.

---

### Post by tagg3rx on 2006-01-12
system > prefs > remote desktop
Check the two top boxes and the require password if you wish

You will probaly want to hard code an IP in
system > admin > networking

or you can get your current IP by typing "ifconfig" in the terminal

FreeNX is a little better option
[https://wiki.ubuntu.com/FreeNX?highlight=%28freenx%29](https://wiki.ubuntu.com/FreeNX?highlight=%28freenx%29)

---

### Post by bensode on 2006-01-12
If you are a command-line person or have the "run" command panel tool enabled, you can start it by invoking **vncviewer** -- I've also pasted the results of vncviewer --help for most of the commandline perameters.  Hope this helps!

bensode@ubuntu:~$ vncviewer --help
VNC viewer version 3.3.7 - built Sep 27 2005 11:12:00
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.

usage: vncviewer [<options>] <host>:<display#>
       vncviewer [<options>] -listen [<display#>]

<options> are standard Xt options, or:
              -via <GATEWAY>
              -shared
              -viewonly
              -fullscreen
              -passwd <passwd-file>
              -noauto
              -encodings <encoding-list> (e.g. "raw copyrect")
              -bgr233
              -owncmap
              -truecolour
              -depth <depth>

---

### Post by evendramin on 2006-01-13
I found the Ubuntu 5.10 native xrealvncviewer (/usr/bin/xrealvncviewer) and finally I can VNC a workstation WinXP.

I was trying a new install (/usr/local/bin/vncviewer) from  [http://www.realvnc.com](http://www.realvnc.com) (3.3.7) but I get the message:

"error while loading shared libraries: libXaw.so.6: cannot open shared object file: No such file or directory"

(Ubuntu 5.10 works with the libXaw.so.7)

Thanks people.

---

### Post by DaMasta on 2006-01-13
[QUOTE=ahessling]On my machine I have under GNOME's Applications -> Internet a link to a Terminal Server Client. I never tried it but it looks like a nice frontend to VNC and it supports AFAIK the RealVNC protocol.
Give it a try.[/QUOTE]
Yes, it work with vnc.

---

