---
title: "How do I edit network settings?"
date: 2009-04-11
forum: General Help
---

### Post by MonsterMaxx on 2009-04-11
I'm coming from the RedHat derivations (RHE, Centos, Fedora) and have just installed mythbuntu 9.

One of the many things I'm struggling with is how to change my network settings (name, domain, ip, etc). The files and tools I'm used to using for this aren't here.

??? 

Thanks in advance

---

### Post by lykwydchykyn on 2009-04-11
I haven't used Mythbuntu in particular, so I don't know if it uses network manager to do the network stuff.  But if you don't want to use network manager you can always just edit /etc/network/interfaces to set the ip/netmask/gateway/broadcast, and /etc/resolv.conf to set the DNS and search domains.  

I'd be surprised if there weren't some GUI tool to do it all, but I'm not sure on mythbuntu in particular.

---

### Post by MonsterMaxx on 2009-04-11
well, what tool works in ubuntu? I'll just install that until I can get a feel for how the files are being changed

---

