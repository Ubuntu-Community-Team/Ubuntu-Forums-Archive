---
title: "SSH Port forwarding - SOCKS Proxy"
date: 2012-10-25
forum: Desktop Environments
---

### Post by m3bik on 2012-10-25
I'm able to surf the internet using a SOCKS proxy configuration in Firefox through a forwarded port in SSH using this command:

```
ssh -fND 8000 user@remote.host
```

This makes localhost:8000 point to my forwarded port and it works great.. I'm trying to take that a step forward and forward that port on the remote.host to another.host so I'd end up with

```
localhost:8000 -> remote.host:8000 -> another.host:8000
```

but it doesn't work if I try that same command on the remote.host to forward it to another.host...

Is this possible to do?

---

### Post by markbl on 2012-10-25
There are a few ways to do that but if another.host is always only accessible via remote.host then you are best to just add the following to your ~/.ssh/config:
```

host another.host
    proxycommand ssh user@remote.host nc %h %p

```

Then you can just directly "ssh -D 8000 another.host" from your first host. Untested, but you can fill in the cracks.

---

### Post by Lars Noodén on 2012-10-26
The proxycommand trick with netcat should do the job.  I have a bit written about that method here:
[http://en.wikibooks.org/wiki/OpenSSH/Cookbook/Proxies_and_Jump_Hosts#ProxyCommand_with_Netcat](http://en.wikibooks.org/wiki/OpenSSH/Cookbook/Proxies_and_Jump_Hosts#ProxyCommand_with_Netcat)

That method is often called a jump host, and there is a fair amount of material about it on the net.

---

