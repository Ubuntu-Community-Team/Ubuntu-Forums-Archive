---
title: "OpenVPN, can't get it running over the internet"
date: 2008-12-19
forum: General Help
---

### Post by Cadmus on 2008-12-19
**The Situation:**
Hello, I'm trying to set up a VPN between a server running Ubuntu Hardy and my live-USB stick running Xubuntu Intrepid.

The VPN worked on my local network, by putting in the local address. So I'm happy that the certificates and the like are correct.

I'm unsure about port forwarding on my router, though when I set the server to use TCP port test websites it came back good (I'd rather use UDP though).

When I try to connect from the usb pen with
```
sudo openvpn /etc/openvpn/client.conf
```

Then it gets as far as 'Connection refused  UDPv4 code=111' or something to that effect and it keeps coming up with that line.  

I know I've not given complete detailsof what happened here (I'm at work), and I'll be giving you more later (as well as trying setting the protocol to TCP)

**The Question:**
I was wondering if anyone else has had problems setting up a UDP OpenVPN and if this is a NAT problem on my router or a firewall problem on the server.

---

### Post by madverb on 2008-12-19
What port is OpenVPN listening on?

---

### Post by Cadmus on 2008-12-19
1194 as per IANA, and that's set in both config files.

---

### Post by madverb on 2008-12-19
and you have that port forwarded on the router?

---

