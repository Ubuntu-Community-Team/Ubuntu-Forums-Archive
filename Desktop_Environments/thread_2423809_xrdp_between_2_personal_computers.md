---
title: "xrdp between 2 personal computers"
date: 2019-07-29
forum: Desktop Environments
---

### Post by tendouser on 2019-07-29
What do I need install to achieve remote desktop connection between to micro-computers (laptops or desktops) both running Xubuntu?
Do I need to install just 'vino' and 'remmina'?

Cheers!

---

### Post by TheFu on 2019-07-29
If the systems are on the same LAN, just use X11's built-in capabilities to run programs on the other machine, but have the window shown on your local machine.
[https://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications](https://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications) explains a multitude of options.

I use **x2go** for needs over the internet. There is a server and a client.  If you want to connect either way, then both will need to run both the client and the server.
x2go feels 2-3x faster than other alternatives and all traffic is encrypted via ssh, unlike the other alternatives, which have zero or really, really, bad encryption, if any.  x2go provides a full desktop, so it isn't nearly as convenient as using X/Windows built-in remote display capabilities.

Before doing anything, setup ssh servers on both machines and get those connections working first.  If they are not always on a secured network, you'll want to secure the ssh server too. This is very well-understood with many guides.  Once ssh is secured, x2go is also secured.

If you are interested in x2go, use their PPA AFTER you get ssh working.

---

