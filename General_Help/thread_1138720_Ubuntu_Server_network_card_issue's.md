---
title: "Ubuntu Server network card issue's"
date: 2009-04-26
forum: General Help
---

### Post by DrDoS on 2009-04-26
Hey Guys,

I am having this weird problem with my one server. After I boot it up the networking works fine - It host's, pings and etc just fine. But after a few hours the networking capabilities stop working.

I have to ifdown eth0 and then ifup eth0 for it to work again.
Does any one have any ideas what might be causing this?

Thanks in advance.

---

### Post by antikristian on 2009-04-26
do you have dhcp or a fixed ip address?

---

### Post by DrDoS on 2009-04-27
> **antikristian said:**
> do you have dhcp or a fixed ip address?

Fixed IP address

---

### Post by antikristian on 2009-04-27
when the problem occurs, first do a ifconfig to see that you still have an ip address on that ethernet connection.

Then ping your local address, for instance, if you have 192.168.5.10 on eth0, ping that address.

If both of those were successfull, then try to ping your gateway. Like for instancee 192.168.5.1. to find your default gateway, run the command "route" and look for the default route, there should be only one.

If you are able to ping the default route, try to ping another computer in your network, and then try to ping a public ip address, like google.com (ping google.com while the connection works, and write down the ip address)


Try this when the connection shuts down, and let me know how far you get:)

---

### Post by DrDoS on 2009-04-27
> **antikristian said:**
> when the problem occurs, first do a ifconfig to see that you still have an ip address on that ethernet connection.

Then ping your local address, for instance, if you have 192.168.5.10 on eth0, ping that address.

If both of those were successfull, then try to ping your gateway. Like for instancee 192.168.5.1. to find your default gateway, run the command "route" and look for the default route, there should be only one.

If you are able to ping the default route, try to ping another computer in your network, and then try to ping a public ip address, like google.com (ping google.com while the connection works, and write down the ip address)


Try this when the connection shuts down, and let me know how far you get:)


Ok - sorry for taking so long to respond. 

I can not ping my gateway. it fails at the gateway - getting Destination host unreachable.

---

### Post by antikristian on 2009-04-28
try to do a ```
route
``` before and after the network goes down. To see if there is anything different between the two.

Even if there's nothing diffrent, post the output of route here

---

### Post by DrDoS on 2009-04-28
> **DrDoS said:**
> Ok - sorry for taking so long to respond. 

I can not ping my gateway. it fails at the gateway - getting Destination host unreachable.


 Before Network Goes Down:
[IMG]http://dev.reflectstudios.com/before.jpg[/IMG]

After Network Goes Down:
[IMG]http://dev.reflectstudios.com/after.jpg[/IMG]

Included a ifconfig as well for you.

---

### Post by antikristian on 2009-04-28
the routing table looks unchanged, but there's quite a few collitions on the ifconfig  output you posted. it might be worth your while to read up on the port speed of your router. 

I remember having similar problems with an old cisco router that only supported 10baseT half duplex. 

The collitions are likely to be related to having network equipment that only support half duplex speeds (or that you are using a hub, the same cisco router I had problems with had a built in hub, not switch)

So my theory is, the router starts with autosensing the connection, gets errors and collitions, tries to autosense your connection speed again, but after a while it fails, and breaks the connection.

So either manually set the connectionspeed on the router, or manually set it lower on the server (try with 100baseT half duplex, or 10baseT half duplex.

To change settings on Linux, looky here [http://www.cyberciti.biz/faq/linux-change-the-speed-and-duplex-settings-of-an-ethernet-card/](http://www.cyberciti.biz/faq/linux-change-the-speed-and-duplex-settings-of-an-ethernet-card/)

I might be wrong, but I think it's somewhat likely that this might be your problem:)

---

### Post by Iowan on 2009-04-28
Of course I can't find it now, but I (vaguely) remember a thread (quite) some time ago about ACPI (or BIOS power savings?) causing problems.

---

### Post by antikristian on 2009-04-28
The problem might also be an autosensing issue on the router, if it senses the port to be half duplex, even if it supports full duplex, then you might get the same problem. If it's possible to manually set the port speed on the router, then you might be able to get 100baseT full duplex without this problem

---

### Post by DrDoS on 2009-04-28
Ok Just to rule this out - I have another server same setup as this and on the same switch - and it has no issue's what so ever and does not drop out. It is just one IP higher. 

If the router is doing the autosensing for the connections woudlent it do the same thing to the other server?

---

### Post by antikristian on 2009-04-29
Is it the exact same network card on that server? in that case, in an ideal world, you should have the same issue on that server. see if this server also get's collitions in the connection. You could try to rearrange the ports on the switch to rule out a faulty port, and switch cables with the other server if possible.

---

### Post by Iowan on 2009-05-01
Built-in NICS, or could you swap them between machines?

---

### Post by blindmist on 2009-08-27
I am having the exact same issues.

It is becoming a pain in the *** because I have to wait to get home to reboot it locally when it pulls this crap.

Any luck on getting this fixed?

---

