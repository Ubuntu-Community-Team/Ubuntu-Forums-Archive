---
title: "?Howto? Ubuntu VNC login"
date: 2005-05-13
forum: Desktop Environments
---

### Post by t3kn0lu5t on 2005-05-13
I would consider myself an intermediate Linux user, and I recently tried Ubuntu and love it.  I have an idea of what I want to do, but I'm not sure how to get there.  Any advice would be appreciated.  :) 

My Ubuntu box is headless, and I want to be able to use VNC or a similiar program to connect to the box and login using the ubuntu login screen.  I setup the vnc server in preferences, but it's only running while I'm already logged in.  This isn't desirable behavior since I don't like to stay logged in, and if there is a power failure or a need to reboot I will have to reconnect a keyboard and monitor just to log back in.

If possible I would like to have multiple users be able to log in at the same time on different VNC/Whatever sessions, but that's totally optional.

I have no idea where to look for info on how to do this to ubuntu. ](*,)

---

### Post by cwaldbieser on 2005-05-14
The following article looks like what yu might want:

[http://linuxreviews.org/howtos/xvnc/](http://linuxreviews.org/howtos/xvnc/)

I am not sure if there is a built in way to get vino (the Gnome VNC program) to do this.  I have had good experiences with xvnc/tightvnc, though.

---

### Post by az on 2005-05-14
look at the ltsp-utils package.  I think this is what you want.  Do not use vnc, but use a thin-client approach with a remote x server and client.

---

