---
title: "How do I setup an SSH server"
date: 2010-07-22
forum: Desktop Environments
---

### Post by JohnElway on 2010-07-22
I have an old computer that I rarely use and would like to turn it into an SSH server. I still use it occasionally, so I want to keep the desktop version of Ubuntu on it. Based on what I've read, all I have to do is install openSSH and, because I'm behind a router, I will need to forward port 22. Is that correct?

Also, on most dedicated servers the server IP address is static, but I'm guessing that the addresses on this computer are dynamic. Is there anyway to change that? And if anyone connects remotely with SSH, I'm assuming they'll have access to my entire computer. Is there a way to restrict access to a single folder? Sorry if these questions sound weird, I've never attempted anything like this before.

---

### Post by fishtoprecords on 2010-07-22
all you need are to install sshd, using Synaptic, apt-get, etc.

If the computer is inside your house, using DHCP, you just need to bind a fixed IP address to the MAC address of its NIC.

Most consumer routers can do this easily.

Yes, you will need access to port 22 into the machine from where ever you want to come from.

---

### Post by mikewhatever on 2010-07-22
> **JohnElway said:**
> I have an old computer that I rarely use and would like to turn it into an SSH server. I still use it occasionally, so I want to keep the desktop version of Ubuntu on it. Based on what I've read, all I have to do is install openSSH and, because I'm behind a router, I will need to forward port 22. Is that correct?

Yes, that's about it. I'd recommend changing the default port to something else, otherwise you get a lot of random login attempts. 2222, 2121, 2323, etc, any of these will do, the config file is /etc/ssh/sshd_config.

> Also, on most dedicated servers the server IP address is static, but I'm guessing that the addresses on this computer are dynamic. Is there anyway to change that? And if anyone connects remotely with SSH, I'm assuming they'll have access to my entire computer. Is there a way to restrict access to a single folder? Sorry if these questions sound weird, I've never attempted anything like this before.

It's advisable to make sure both internal and external IPs are static. The former can be configured with the Network Manager, and the latter with serices like [http://www.dyndns.com/](http://www.dyndns.com/) or [http://www.no-ip.com/](http://www.no-ip.com/).
As for restricting to a folder, connect as non-privileged user and you'll be restricted to your home folder.

---

### Post by halfshellheroes on 2010-07-22
I set up an ssh server today on my old dell box. I just followed this guide, everything worked beautifully.

[http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/](http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/)

---

