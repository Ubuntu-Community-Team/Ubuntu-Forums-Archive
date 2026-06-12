---
title: "networkmanager applet reports 'device not managed'"
date: 2011-01-10
forum: Desktop Environments
---

### Post by danieru on 2011-01-10
Greetings,
I'm trying to build a simple and lightweight ubuntu desktop. I'm playing around in a Virtualbox VM first to find the setup I like, then I'll roll out to an old laptop I have.
I've started with the Ubuntu 10.10 32bit CLI install, then from there I installed the packages (via aptitude): 
-network-manager-gnome
-lxde

...with all their dependencies of course.

I enabled 'Network Manager' in the lxde desktop session settings, and the applet is appearing (well, it's invisible, but it is there; i'll get to that in a moment) but it reports the the wired device is not manageable (see attached screenshot). 
I know that the virtual NIC inside the VM is functioning properly, since I downloaded updates during install, ifconfig shows eth0 up w/ an IP address, etc.  Also, I've installed vanilla Ubuntu in another VM w/ the same settings and the applet manages the NIC just fine, so I think that I'm missing some kind of dependency or configuration step for the applet to manage the interface properly. I also saw this exact same behavior when I was playing around with fluxbox on a similar CLI setup, so I don't think it's related to the window manager. Note also that the applet is invisible, that is, it's not showing an icon for the active connection. (see attachment)

So any suggestions on this? is it a permissions problem, or something else? Any help is welcome:)

---

### Post by danieru on 2011-01-11
Figured it out!

I found this thread [here]("http://forums.debian.net/viewtopic.php?f=10&t=56810"), where it was suggested to do this:

> Check /etc/network/interfaces

It should only contain:

```
auto lo
iface lo inet loopback
```

Comment out the rest!

...and that solved it!  In retrospect it makes sense now, since it's a CLI install, it's assuming you want to manage the NIC via the interfaces file, so there was an entry in there for eth0, which made the network-manager unable to manage it. woot.

---

