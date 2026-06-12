---
title: "How do I close a listening port?"
date: 2005-12-10
forum: General Help
---

### Post by Threepwood on 2005-12-10
```

netstat -l
Active Internet connections (only servers)
tcp6       0      0 *:1234                  *:*                     LISTEN

```

What would be the command to close port 1234?

Thanks

---

### Post by amohanty on 2005-12-11
Do you know what program is using port 1234?

If not try nmap
> 
sudo apt-get install nmap
sudo nmap -vV -sS -p 1234 <your ip address>

HTH

---

### Post by ape on 2005-12-11
you can also install lsof and run the following:

  `sudo lsof -i tcp:1234`

This should tell you what program has this port open.

---

### Post by Threepwood on 2005-12-11
Thanks!  lsof was what I was looking for

---

### Post by lcg on 2005-12-11
[QUOTE=ape]you can also install lsof and run the following:

  `sudo lsof -i tcp:1234`

This should tell you what program has this port open.[/QUOTE]
You don't really need lsof for that. Just run ```
netstat -lp
``` to get a list of the open ports and the processes listening on them.

Lars

---

### Post by ape on 2005-12-12
Well, that's the great thing about UNIX in general... there's more than one way to do things.  I find that lsof give me more information about a port that what `netstat -lp` will give me.  Therefore, that is what I suggested.<G>

---

### Post by lcg on 2005-12-12
[QUOTE=ape]Well, that's the great thing about UNIX in general... there's more than one way to do things.  I find that lsof give me more information about a port that what `netstat -lp` will give me.  Therefore, that is what I suggested.<G>[/QUOTE]
And I only wanted to point out, in case lsof is not available, one can still use 'netstat -lp' (or 'netstat -tulpen', which I prefer, especially because I can easily remember this one).

But then again, if you worry about open ports, you are usually root and then lsof is only an 'apt-get install' away. :)

Lars

---

### Post by tomski on 2005-12-12
so how do we close a port ?

or should we say drop an established connection
or 
is this what a firewall does for us; if so how?

---

### Post by ape on 2005-12-13
How true...:)

---

### Post by lcg on 2005-12-16
[QUOTE=tomski]so how do we close a port ?[/QUOTE]
First of all, on Ubuntu all ports are "open" by default, i.e. no filtering is done. However, as no application is listening on these ports, the kernel automatically rejects any connection attempt. In this case, a port filter doesn't add any security.

If you install an application which is listening for incoming connections (e.g. Apache, ...), there are essentially two possibilities: 1.) You want to offer this service to the outside world. In this case, there's no sense in closing the port with a port filter. 2.) You do not want to offer the service. Why install it in the first place? And if you only want to offer it to some machines on an internal network, you should find out how to make it only listen on a certain network interface.

[QUOTE=tomski]or should we say drop an established connection[/QUOTE]
How should that work? If a connection has already been established, what should trigger a sudden invalidation of the connection?

[QUOTE=tomski]is this what a firewall does for us; if so how?[/QUOTE]
Actually, a firewall can't do anything. Contrary to popular belief, a firewall is not a piece of software. Strictly speaking, a firewall is a security concept which is usually implemented in software.

So, the first step is to write down a policy of what kind of network traffic you want to allow or deny. Then you need to find out how this policy can be implemented; usually the answer will be netfilter if you're using Linux.

There are programs available like firestarter or shorewall but they are actually only frontends for iptables/netfilter. You still need some kind of policy, otherwise there is no security to gain from them.

Hoping this helps to clarify the concept of firewalls and port filters,
Lars

---

