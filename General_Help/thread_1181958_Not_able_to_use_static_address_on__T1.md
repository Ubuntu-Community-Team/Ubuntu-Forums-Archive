---
title: "Not able to use static address on  T1"
date: 2009-06-08
forum: General Help
---

### Post by tookey on 2009-06-08
I have installed Ubuntu server v9 and am planning on using it essentially as a router for my office.  The previous setup is a t1 line that controls our internet/phones.  For the internet the feed went into a Netgear router, which was configured with our static address information.

When I build the server, and configured it with the same address info from the netgear router I get nothing.  I am not able to successfully ping anything.

---

### Post by sabre2th on 2009-06-08
What exactly did you do to set it up?

I'm not an expert, but I've got static IPs set up on my home network.  As far as I know, it should only require editing two files.

It'll depend on your hardware, but '/etc/network/interfaces' should be something close to this:
```
auto lo
iface lo inet loopback

auto eth0
#iface eth0 inet dhcp
iface eth0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.xxx
```Then '/etc/resolv.conf'
```
nameserver  192.168.0.xxx
domain yourdomain
search yourdomain
```

The domain stuff might not be necessary, but I included it anyway...

Fill in your IP info, restart networking with '/etc/init.d/networking restart', and all should be good.  If it still doesn't work, try a full restart.  If the settings won't stick, you can try removing 'dhcp-client'.

---

### Post by tookey on 2009-06-09
Thanks for the response... like an idiot I was looking at an old email from the ISP that had the wrong IP address!!!

---

### Post by sabre2th on 2009-06-09
No problem.  Good to hear you've sorted it out.

---

