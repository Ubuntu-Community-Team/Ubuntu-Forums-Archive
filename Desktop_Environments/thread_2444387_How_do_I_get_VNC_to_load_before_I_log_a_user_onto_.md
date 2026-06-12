---
title: "How do I get VNC to load before I log a user onto Ubuntu 20?"
date: 2020-05-29
forum: Desktop Environments
---

### Post by richardi99 on 2020-05-29
I now have RealVNC working well with Ubuntu 20 desktop.  It restarts at reboot. Provided, that is, I have logged in first.
I want to be able to VNC into the Ubuntu box before I have logged on - and choose which user to log on.  How can I do that?
Thanks

---

### Post by richardi99 on 2020-06-01
Anyone?

---

### Post by TheFu on 2020-06-01
I don't use VNC. Cannot help with that. Sorry, but since you bumped ... 

I use **x2go** where this isn't an issue.  x2go feels 2-3x faster than any VNC.  It uses ssh to tunnel all traffic, so setup ssh between the client and server first.  There are x2go clients for Linux, OSX and Windows.  I know that the Windows and Linux clients are extremely stable.

On the server:
[LIST=1]
[*]```
sudo apt install openssh-server fail2ban
```
[*]Server x2go instructions: [https://wiki.x2go.org/doku.php/doc:installation:x2goserver](https://wiki.x2go.org/doku.php/doc:installation:x2goserver)
[/LIST]

On the client:
[LIST=1]
[*]```
sudo apt install openssh fail2ban
ssh-keygen -t ed25519  # create a strong key-pair
ssh-copy-id -i ~/.ssh/id_ed25519.pub userid@remote   # push the public key to the server
ssh userid@remote  # test the ssh is working
```
[*]Client x2go Instructions: [https://wiki.x2go.org/doku.php/doc:installation:start ](https://wiki.x2go.org/doku.php/doc:installation:start )
[/LIST]

Those ssh keys are used by all ssh-based tools.  ssh, scp, sftp, rsync, sshfs, and 50 others. That includes x2go.
If you setup a ~/.ssh/config file on the client, then ssh connection parameters like a different userid, server IP address, non-standard ssh-port, will all be picked up.

Basically, 5 minutes of effort.

Run the x2go client, point it at the x2go server.  Tweak the connection parameters - I use ISDN for connections over the internet and LAN only when using wired ethernet on the same LAN.  I usually set the image compression to 4K-png. This makes for a very fast connection compared to the defaults.

x2go doesn't play well with heavy DEs like gnome3. Use LXQt, Mate, Cinnamon, or XFCE instead. This assumes you've configured the 20.04 system for one of those others.  Or you can skip the DE completely and use a pure Window Manager only setup.  I use fvwm - crazy fast, crazy configurable.

x2go will change your life. I switched in 2014 (it seems).

---

