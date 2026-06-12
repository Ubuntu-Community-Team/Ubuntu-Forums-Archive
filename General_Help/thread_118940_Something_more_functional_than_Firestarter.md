---
title: "Something more functional than Firestarter"
date: 2006-01-18
forum: General Help
---

### Post by PryGuy on 2006-01-18
Hello everybody!
I'm looking for a firewall software to make a move for my server to Ubuntu. Please recommend me something more functional than Firestarter. It's nice and all but it's pretty similar to Windows Firewall in it's functionality (probably I'm wrong, I was playing with it 10 minutes only). And that's not enough for me! I want something more such as proxy server, traffic limitations, etc.

---

### Post by 23meg on 2006-01-18
Firestarter isn't "firewall software" per se but a frontend to [iptables]("http://www.netfilter.org/projects/iptables/index.html"), which in turn is the command line program used to control the kernel's IP traffic routing rule set. I haven't understood what functionality of Firestarter you've found limiting but in any case, if you want more flexibility you can use iptables directly. You can start learning about it with```
man iptables
```.

---

### Post by PryGuy on 2006-01-18
Okay, I certainly will, but just tell me in two words then, will the iptables allow me do the following things:

- IP based traffic control and limitation
- Traffic statistics
- Proxy server
- Access the user stats through the client browser

---

### Post by 23meg on 2006-01-18
> - IP based traffic control and limitationYes
> - Traffic statisticsNo
> - Proxy serverNo
> - Access the user stats through the client browserNo

---

### Post by SickTwist on 2006-01-18
[QUOTE=PryGuy]Okay, I certainly will, but just tell me in two words then, will the iptables allow me do the following things:

- IP based traffic control and limitation
- Traffic statistics
- Proxy server
- Access the user stats through the client browser[/QUOTE]

[Squid]("http://www.squid-cache.org/") is a proxy server for Linux.

---

### Post by Mr. Electric Wizard on 2006-01-18
Why not use an old throw down computer and run IPCop or Smoothwall...
Very flexible hardware/software firewalls.

---

### Post by 23meg on 2006-01-19
> **SickTwist][Squid]("http://www.squid-cache.org/") is a proxy server for Linux.[/QUOTE]
I was going to say that but I was constrained to two words and if I said "Squid" I'd have only one of "yes" and "no" left.

Now that others have said other words..
> - Proxy serverI'm not sure what you mean said:**
> - Traffic statistics
Use netstat. 
> - Access the user stats through the client browserYou could perhaps route netstat's output via I/O redirection to a simple http server daemon to accomplish that the *nix way.

---

### Post by steve.horsley on 2006-01-19
For statistics, have a look at ntop. It's in the Universe repository.

---

