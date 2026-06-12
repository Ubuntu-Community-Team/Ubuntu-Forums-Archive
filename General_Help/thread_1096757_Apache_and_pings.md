---
title: "Apache and pings"
date: 2009-03-15
forum: General Help
---

### Post by The Joe on 2009-03-15
I have a no-ip address pointing to a server I am running on my home PC (so I can listen to music at school) but I noticed that pinging it is potentially dangerous. It brings up my host and IP.

Is there a way at all I can block these or replace them with something else, because presumably running a port 80 server opens a few holes, right? Just thinking it would be a good idea to stop the pings somehow or tell them to go somewhere else.

---

### Post by The Joe on 2009-03-15
Hmm. Bump.

---

### Post by The Joe on 2009-03-15
Sorry to keep bumping but I wouldn't need to if someone answered ^_^

---

### Post by snova on 2009-03-15
> **The Joe said:**
> I have a no-ip address pointing to a server I am running on my home PC (so I can listen to music at school) but I noticed that pinging it is potentially dangerous. It brings up my host and IP.

I don't think there's anything you can do about that. Finding your IP address has nothing to do with pings, since you have to know the IP before you can ping in the first place. :)

It's DNS that's the problem- No-IP redirects to your "real" hostname, which can then be looked up to find your IP address. There might be something you can do, but I think it would be with No-IP, not with your server.

> Is there a way at all I can block these or replace them with something else, because presumably running a port 80 server opens a few holes, right?

I don't think the server itself is a problem, more so what you put *on* the server...

> Just thinking it would be a good idea to stop the pings somehow or tell them to go somewhere else.

There is a way you can make your server ignore all pings, but it won't hide your IP. I found it here: [http://ubuntuforums.org/showthread.php?t=854074](http://ubuntuforums.org/showthread.php?t=854074)

---

### Post by Gunman1982 on 2009-03-15
Furthermore you could configure the webserver to listen on a different port (i.e. port 2080) to fool many of those automatic sniffers in the net. If you don't know how to access it anymore after the change try 'www.your.no-ip.address.com:2080' where the part behind the : is the port where the server listens.

---

### Post by bodhi.zazen on 2009-03-16
> **The Joe said:**
> I have a no-ip address pointing to a server I am running on my home PC (so I can listen to music at school) but I noticed that pinging it is potentially dangerous. It brings up my host and IP.

Is there a way at all I can block these or replace them with something else, because presumably running a port 80 server opens a few holes, right? Just thinking it would be a good idea to stop the pings somehow or tell them to go somewhere else.

You will get different opinions, but IMO replying to a ping is a minimal risk, less so on a public server.

If you wish to block pings you can do do via iptables.

```
iptables -A INPUT -t icmp -j DROP
```

If you wish you can use ufw, gufw, or another tool to configure iptables.

```
sudo ufw enable
```

See also [https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw](https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw)

---

