---
title: "[SOLVED] remote log in"
date: 2008-12-12
forum: General Help
---

### Post by flytripper on 2008-12-12
hi peeps.

I was wondering if remote desktopping in to an ubuntu machine was possible from an xp client when the ubuntu machine is in its just booted and at the login state?

i know this is possible in windows as i used to remote from my main pc to my netbox (stored in my loft) which i was using to handle my torrents and file streaming to my 360 so as to free up my main pc for gaming and stuff.

can i use microsoft terminal services console or do i need more software?

thanks in advance

---

### Post by Sjeti on 2008-12-12
I know you can use NX Server on the ubuntu and the freenx-client on your windows box.

Its a nice remote desktop program, I use it for work.

---

### Post by flytripper on 2008-12-12
will look into it,, but does it enable me to remote in without first having to log onto the ubuntu machine(server)?

---

### Post by geirha on 2008-12-12
Yes, unlike VNC, you don't take control of an already logged in session. It opens a new session for the username and password you provide.

---

### Post by HermanAB on 2008-12-12
The better way is to install OpenSSH-Server package.  VNC is almost always the wrong answer for Linux.  

You can connect to a SSH server from windows using the PuTTY and Xming programs.

Cheers,

Herman

---

### Post by geirha on 2008-12-12
> **HermanAB said:**
> The better way is to install OpenSSH-Server package.  VNC is almost always the wrong answer for Linux.  

You can connect to a SSH server from windows using the PuTTY and Xming programs.


That's how FreeNX works. It connects with ssh, starts an Xsession on the remote computer and has some added compression magic so it works a bit faster than regular X11 forwarding.

---

### Post by asker on 2008-12-12
I am using the NX cliet on a Windows machine in Germany to connect to a linux NX server in America... Way faster than VNC.

---

### Post by flytripper on 2008-12-12
sorted.. thanks everyone

---

