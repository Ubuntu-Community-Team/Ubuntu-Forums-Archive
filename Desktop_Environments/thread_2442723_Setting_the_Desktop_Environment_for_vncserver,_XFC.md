---
title: "Setting the Desktop Environment for vncserver, XFCE -&gt; Ubuntu Desktop"
date: 2020-05-06
forum: Desktop Environments
---

### Post by sdscotti on 2020-05-06
I just started using Ubuntu again, this time with a dedicated server.  Usually a Mac user, so LINUX skills are a little rusty.  The server is pretty much bare bones to start with.  I would like to setup a VNCserver, and I started doing that with I think TightVNC.  I also installed Ubuntu Desktop using apt, so that also should be on my system.  I had to configure some stuff so that I can ssh into the server and use a VNC client.  That is working, so I have an SSH connecting to the VNC server, but I am still getting the XFCE desktop.  I am sure that is lighter wait and probably better for a VNC connetion, but I would like to have the option of using UBUNTU desktop.

In ~/.vnc/xstartup I have this:

#!/bin/bash
xrdb $HOME/.Xresources
startxfce4 &

How can I change that so that I get my other desktop manager to be the default ?

The packages that I installed are:

sudo apt-get install ubuntu-desktop

apt install tigervnc-standalone-server tigervnc-common tigervnc-xorg-extension tigervnc-viewer

sudo apt install xfce4 xfce4-goodies

Probably just need to set that to use Ubuntu Desktop, but not sure how to do that.  Thanks.

---

### Post by TheFu on 2020-05-07
a) use an ssh tunnel.  Remote VNC or RDP are not safe enough for use over the internet.  vncserver has an option to only allow localhost connections, which is a method to ensure that the network connection is to the localhost before allowing any VNC.  My previously working in 2010 VNC has this:
```
~/.vnc$ more xstartup
#!/bin/sh

xrdb $HOME/.Xresources
xsetroot -solid grey  # set the root background.
 
/usr/bin/xterm -sb  &    # always want an xterm, even if everything else fails.
export XKL_XMODMAP_DISABLE=1   # DEs have lots and lots of mandatory environment variables.
/usr/bin/gnome-session 
```

OR

b) use x2go, which uses the NX protocol that includes ssh tunneling and authentication and has better performance than other free options.  You get good security, only the ssh port is used, ssh-keys can be used (and should be used over the internet), and 2-3x better performance than VNC provides.  There is an x2go PPA from the project team.  Everyone who has changed to x2go says it is like finally being in daylight rather than night.

If you want an xfce4 desktop, then you can install either the full meta package or just the DE.  If you really want a faster environment, use a pure WM solution like openbox or fvwm. Those are smaller and faster than any DE.

**apt search xfce4** found this: 

```
xfce4/xenial,xenial 4.12.2 all
  Meta-package for the Xfce Lightweight Desktop Environment
``` 
along with many, many, other xfce4 specific packages - ran it on a 16.04 system.

On 20.04, 
```
xfce4/focal,focal 4.14 all
  Meta-package for the Xfce Lightweight Desktop Environment
```

The VNC trick is to launch the WM+DE in the vncserver script.
The x2go trick is to select XFCE from a drop down on the client-side.  Of course, setup ssh first so x2go works easily.

---

