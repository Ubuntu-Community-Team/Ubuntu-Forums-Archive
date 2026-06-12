---
title: "Start Gnome on a headless server?"
date: 2008-12-12
forum: General Help
---

### Post by comspy on 2008-12-12
I am looking for a way to start GNOME on startup, even without a monitor. I plan to access GNOME through remote desktop. Any help would be very appreciated.

---

### Post by geirha on 2008-12-12
One way to do it is with XDMCP. First ssh into the box with X11forwarding, and run gdmsetup

```

ssh -X user@host
sudo gdmsetup

```

and enable remote connections.

On the client, install [xnest](apt://xnest), then connect with Applications -> Internet -> Terminal server client.

Another option is [FreeNX](https://help.ubuntu.com/community/FreeNX).

---

### Post by comspy on 2008-12-12
I'm getting confused with x11forwarding. There is no way to have ubuntu just startx and login normally without a monitor and me be able to screen share with it with my Mac?

---

### Post by tgalati4 on 2008-12-12
You can boot to a console on the server.  Don't need graphics running on a headless box.  

Install open-ssh and log in from a remote machine:

>ssh -2 -Y youruser@yourservername
(password)

YourServer> gnome-panel

---

### Post by comspy on 2008-12-13
> **tgalati4 said:**
> You can boot to a console on the server.  Don't need graphics running on a headless box.  

Install open-ssh and log in from a remote machine:

>ssh -2 -Y youruser@yourservername
(password)

YourServer> gnome-panel


Thanks for your help! That worked!

---

