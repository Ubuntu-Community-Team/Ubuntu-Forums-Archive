---
title: "Top menu bar not loading when remotely connected"
date: 2012-08-25
forum: Desktop Environments
---

### Post by Ortix on 2012-08-25
So i recently installed Ubuntu 12.04 desktop on my home server and loving it so far. The only problem is that when I  try to connect remotely to the desktop (be it vnc, nx or rdp), nothing would show up except for the background. If I had a window open, it would show up but that's it. So no icons on the side or menu bar (I'm not familiar with the ubuntu terms yet, unity maybe?)

I managed to get the sidebar going by creating an .xsession file with the following content:

```
gnome-session --session=ubuntu-2d

```But that just makes the sidebar appear, the top menu bar is still gone.

Currently I'm using RDP to connect to the server (i'm connecting locally through LAN) with xRDP installed.

So if anyone could help me out of this pickle.. i would really appreciate it!

BTW, I did try searching on google, but I have no idea what those bars are called so I ended up searchign with keywords such as "remote desktop ubuntu menu bar not working" but that obviously wouldn't give me any luck :lolflag:

---

### Post by TheFu on 2012-08-25
Remote desktops are not the same as local desktops, especially now that 3D and 2D accelerated graphics is required.  I don't know the answer or work-around, but just wanted to share the "why" with you.

You can always open a terminal and type the name of the program you'd like to run. The $PATH works exactly the same.

BTW, congrats on using NX. Best remote desktop protocol out there that works easily.  Soon (months or a year), SPICE will be easily available and completely change remote desktops.

---

### Post by Ortix on 2012-08-29
Anyone able to help me with this?

---

### Post by TheFu on 2012-08-29
I'm still not certain that I understand what you want, but this might help:
[http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications](http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications)

If you are looking for Unity in a remote desktop, I don't think that is possible.
If you can live with Gnome2 or LXDE or a simple right-click menu anywhere, then you can use any window manager you like.  

Your remote desktop "server" simply needs to be setup to run whatever you choose. VNC server is probably what you are using on Linux, not RDP.   Something like this will work: [http://forum.lxde.org/viewtopic.php?f=3&t=31126](http://forum.lxde.org/viewtopic.php?f=3&t=31126)

If the programs that you run demand GPU 2D or 3D accel and you are connected over a VNC, RDP or NX session, I don't know what the result will be, but suspect either a blank background OR a crash of VNC/RDP/NX at the client or server.

X/Windows has a remote desktop feature built-in. It is called XDMCP. [https://wiki.ubuntu.com/xdmcp](https://wiki.ubuntu.com/xdmcp) I've never used it on Ubuntu, but it works for all the other X/Windows systems I've used - AIX, Solaris, SunOS, HP-UX, Irix, ...   Only use this on a LAN, never on a WAN. It uses lots of bandwidth.

---

### Post by Ortix on 2012-08-29
Well I'm trying to get the unity menu bar (The top gray bar) to appear. When I log in, it appears for a second or two and then disappears. Currently I have this in my .xsession file:
gnome-session --session=unity-2d

this gives me the unity bar on the SIDE but not on the TOP. Not sure what that bar on the top is called so i'll just call it top menu bar.

When I try to restart unity i get the following error:

compiz (core) - Fatal: No XKB extension
unity-panel-service: no process found

I just find it hard to believe that it's impossible to get the top bar to appear if i can get the side bar to appear.

EDIT:
After a couple of restart of the xrdp server, the top bar magically did not crash and is working.. very odd

---

### Post by TheFu on 2012-08-29
> **Ortix said:**
> When I try to restart unity i get the following error:

compiz (core) - Fatal: No XKB extension
unity-panel-service: no process found

Compiz requires an accelerated graphics adapter to work. That cannot work with current remote desktop solutions.  Perhaps it will with SPICE when that becomes stable in the future, but not today.

The fact that you got something working means that it broke something else in the process.

---

### Post by shickster on 2013-03-06
I found the solution here [https://bugs.launchpad.net/ubuntu/+source/nux/+bug/889996](https://bugs.launchpad.net/ubuntu/+source/nux/+bug/889996)

---

