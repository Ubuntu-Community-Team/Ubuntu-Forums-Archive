---
title: "Permissions issue with Network Control Panel (Mate on AWS EC2)"
date: 2017-07-06
forum: Desktop Environments
---

### Post by Nunnsby on 2017-07-06
I seem to have a weird permissions error that I am unable to resolve. I have installed Ubuntu Mate on an AWS EC2 instance following these awesome steps here: [https://alexanderzeitler.com/articles/deploying-ubuntu-mate-desktop-as-developer-environment-on-aws-ec2/](https://alexanderzeitler.com/articles/deploying-ubuntu-mate-desktop-as-developer-environment-on-aws-ec2/). I have followed them to a tee and the user has the required permissions, but I notice the main thing is that Sound and Network Icons are greyed out in the panel. Also, I suspect for this reason, I cannot get OpenVPN to work. I have installed the gnome add-on for OpenVPN and configured/imported a profile fine.

1) Sound I suspect is due to no sound driver (not a linux guru so I stand to be corrected), even though it states 100% when you hover over it.

2) Networking doesn't show an adapter. I can click on Edit, and when I do I don't see an adapter in there. I originally didn't have an OpenVPN connection in there either so I followed the instructions and installed the gnome openvpn add-on.
I then had to follow the recommendation of using the sudo nm-connection-editor to import the OpenVPN profile. 
Using the standard way (without sudoing the nm-connection-editor from the cmd line) I could import the profile, but not save it. 
Using sudo nm-connection-editor from the command line I could import it and save it, but when I click on the profile via the control panel, it shows connected, but it is not. 

Any advice? I suspect it is a permissions error somewhere. But where?

Thanks

---

### Post by TheFu on 2017-07-07
Forget the GUI, for now.

If I were doing this, I'd use an NX remote desktop like x2go, not VNC or rdp.   NX uses ssh - ssh tunneling is part of the protocol and authentication. It uses the same ssh you need already for the 50 other things every Unix person wants.  Same ssh port, same ssh-keys, same normal firewall rules and you can use denyhosts or fail2ban. Plus x2go feels 2-3x faster than either VNC or RDP.  I don't know about audio working over a WAN connection, but it definitely works on the same LAN.

With ssh - always used keys, never passwords, over the internet.  Oh - use the password once, to setup the keys, then disable password access to ssh from remote systems. It is an important security thing.

BTW, I've used x2go from CPT (and lots of other places in the world) back to my private cloud in the USA.  Works fine for productivity applications.  You won't be watching videos - but you won't be doing that with any remote desktop. 
x2go has clients for Windows, Linux and OSX.  I know the Linux and Windows clients work well.  Just be certain to setup and get ssh working first, BEFORE touching any x2go stuff.

People who try x2go say it is like comparing night (rdp/vnc) to day (x2go/NX).  That has been my experience too, though I haven't bothered with the other methods in 5+ yrs.

As for networking, if the network is setup with static data, then you'll have to deal with those files.  /etc/network/interfaces is normally used.  The output from ifconfig and route would confirm that.

For openvpn - I use it as a client.  No GUI, just a little start/stop script and config files.  I've never used the GUI for it, so probably cannot help with that aspect.  Setting up an openvpn client isn't hard with config file settings. Most commercial providers will have example config files.  If you want to run your own, I'd look at one of the freeSwan forks to get an IPSec VPN.

If the VPS provider was using KVM, then you could use the Spice remote desktop. It is designed to be "wire speed" for everything.  I've seen it used over a WAN connection, but never set it up successfully.  Security seems to be an afterthought for it.

---

### Post by Habitual on 2017-07-07
> **Nunnsby said:**
> Any advice? I suspect it is a permissions error somewhere. But where?
I doubt it. Those Images aren't really ready for desktop features like sound.

---

