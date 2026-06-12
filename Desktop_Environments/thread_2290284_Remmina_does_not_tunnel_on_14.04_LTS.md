---
title: "Remmina does not tunnel on 14.04 LTS"
date: 2015-08-11
forum: Desktop Environments
---

### Post by Lars Noodén on 2015-08-11
In 14.04 LTS, Remmina can connect to VNC over an existing tunnel but seems not able to create its own tunnel.  If I launch a VNC server on a remote machine and forward the appropriate ports,

```

ssh -L 5900:localhost:5900 *xx.xx.xx.xx* 'x11vnc -rfbauth ~/.vnc/passwd -localhost -display :0 -noxdamage -ncache 10'

```

then I can connect with Remmina to VNC as localhost:****0

However, if I do not create the tunnel in advance,

```

ssh *xx.xx.xx.xx* 'x11vnc -rfbauth ~/.vnc/passwd -localhost -display :0 -noxdamage -ncache 10'

```

Then there is nothing that I can find (so far) that allows me to use Remmina to create the tunnel.  

Protocol -> VNC

Basic->Server->localhost:0

SSH
 ->Enable Tunnel
      ->Tunnel via loopback address
    ->Server->Custom->*xx.xx.xx.xx*


It asks for the SSH password, X11vnc shows that there is a connection, then Remmina asks for the VNC password, it accepts the password and briefly opens a window but closes it before anything can render.  The VNC server says only 'viewer exited'

How can I get Remmina to connect with VNC over an SSH tunnel of its own creation?

---

### Post by steeldriver on 2015-08-13
Hmm... I could swear that it worked when I first installed 14.04

I tried it yesterday on a LAN connection with standard SSH port 22, and it seemed to work, but NOT over a WAN to a box with non-standard SSH port. Perhaps that's significant, perhaps not (that box is having some authentication issues, although I am currently connected to a tunneled tightvnc session from Windows using putty and tightvnc viewer)

I will try again and update if I find anything relevant

On a side note, I found remmina to be generally flaky in the last little while (hangs, grays out the display, has to be killed)

---

### Post by Lars Noodén on 2015-08-13
Yeah, I thought it used to work, too, but version 1.0.0-4ubuntu3 seems not to tunnel.  Along the same lines it looks like it might be using outdated, insecure key exchange methods and ciphers, but I haven't looked closely at that yet.

What's the best replacement?  Remmina is in the default installation in Ubuntu and I think Xubuntu.

---

