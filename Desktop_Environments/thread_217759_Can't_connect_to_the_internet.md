---
title: "Can't connect to the internet"
date: 2006-07-17
forum: Desktop Environments
---

### Post by ardchoille on 2006-07-17
I have an issue that I would say is more of an annoyance than a problem.

Have a look at this:

```

[~ @ 11:58:09] cat /etc/resolv.conf
search domain.actdsltmp
nameserver 192.168.0.2
nameserver xxx.xxx.xxx.xxx

```
I x'd out the second nameserver line for security reasons, not even sure I needed to do that. 192.168.0.2 is the router IP.

My problem is something (app/script) keeps putting "nameserver 192.168.0.2", which is the ip of my router, back into /etc/resolv.conf during boot/reboot. When that happens, I cannot connect to the internet at all until I do "sudo sed -i 's/nameserver 192.168.0.2//g' /etc/resolv.conf". Once I take the 192.168.0.2 line out of /etc/resolv.conf, I can connect again.

I realise I can take the 192.168.0.1 line out of resolv.conf and sudo chattr +i /etc/resolv.conf so that even root can't modify the file anymore, but I would like to know which app/script keeps putting the router IP back into resolv.conf. I would also like to know how to prevent that from happening in future boots/reboots.

Any ideas?

---

### Post by wahman143 on 2006-07-17
Hi,
I think the network init script does that - assuming you have your ethernet set to pick up via DHCP.  I know on Gentoo you can add a line in your network config that tells ethernet0 not to pickup DNS from the DHCP server, but I'm not sure if ubuntu uses the same connotation.

Sorry I couldn't be more specific, but I do think DHCP is setting it to your router address.

HTH,
W.

---

### Post by ardchoille on 2006-07-17
> **wahman143 said:**
> Hi,
I think the network init script does that - assuming you have your ethernet set to pick up via DHCP.  I know on Gentoo you can add a line in your network config that tells ethernet0 not to pickup DNS from the DHCP server, but I'm not sure if ubuntu uses the same connotation.

Sorry I couldn't be more specific, but I do think DHCP is setting it to your router address.

HTH,
W.

Thank you for the reply, this is a start. How do I find the script you are talking about, filename? Is there an app I need to run to configure this?

I tried man dhcp and there is no man page for it.

---

### Post by wahman143 on 2006-07-18
> **ardchoille said:**
> Thank you for the reply, this is a start. How do I find the script you are talking about, filename? Is there an app I need to run to configure this?

I tried man dhcp and there is no man page for it.
Hi - the file in question is /etc/network/interfaces and the man page is man interfaces - however, I'm not finding that option available...so let me keep looking.

Despite that, the interfaces file is where you can statically set your IP address, so I'd try setting it that way and also editing your /etc/resolv.conf file to your liking - and see what happens now that you've set the IP info manually.

I'll let you know if I find that option.

Cheers,
W.

---

### Post by ardchoille on 2006-07-18
> **wahman143 said:**
> Hi - the file in question is /etc/network/interfaces and the man page is man interfaces - however, I'm not finding that option available...so let me keep looking.

Despite that, the interfaces file is where you can statically set your IP address, so I'd try setting it that way and also editing your /etc/resolv.conf file to your liking - and see what happens now that you've set the IP info manually.

I'll let you know if I find that option.

Cheers,
W.

Well, manually editing /etc/network/interfaces seemed to work. Thank you for the help :)

---

