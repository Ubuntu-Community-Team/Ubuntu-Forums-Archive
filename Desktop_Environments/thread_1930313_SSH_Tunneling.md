---
title: "SSH Tunneling"
date: 2012-02-23
forum: Desktop Environments
---

### Post by DanHorniblow on 2012-02-23
I need to tunnel all of my http traffic coming into to my desktop through a dedicated server that I have.

I can do this by running:

```
ssh -D 9999 -C root@servername -p port
```

and then telling fire fox to use localhost on port 9999.

But I also need to tunnel my dns from my desktop through the same server to a public dns service such as google or opendDNS.

I am stuck on how to tunnel the DNS.

Any suggestions?

---

### Post by gradinaruvasile on 2012-02-23
Ummm... Why do you need to tunnel DNS? What prevents you from using it directly?
As a matter of fact, why do you need all this? Routing is done via iptables usually. Ssh is not made for this kind of stuff.

---

### Post by Lars Noodén on 2012-02-23
For just Firefox, you need to set  [font=Courier New]network.proxy.socks_remote_dns[/font] to true.  You can find it if you enter the URI [font=Courier New]about:config[/font] in the address bar.

---

