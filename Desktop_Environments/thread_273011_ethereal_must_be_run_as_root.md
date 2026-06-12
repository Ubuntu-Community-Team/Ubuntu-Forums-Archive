---
title: "ethereal must be run as root?"
date: 2006-10-07
forum: Desktop Environments
---

### Post by styracosaurus on 2006-10-07
Hi I am using Ethereal to debug a BitTorrent program I am working on for a class, but I must run it as root to be able to capture from eth0 or any interface at all. When I run as regular user no interfaces are listed, while when I run as root I can see the interfaces. I installed Ethereal from the official Ubuntu repositories.

I think this is a pretty common problem, there seemed to be a lot on it else where on the Internet, but I wondered if someone could explain why this is and how to fix it specifically in Ubuntu. Sorry if this has been addressed before, but I didn't see anything about it when I searched this forum.

Thanks.

---

### Post by lamego on 2006-10-07
ethereal needs to be run as root because in order to trace the network traffic he needs to setup the network card promiscuous mode, thats a setting that only a privileged user can change.

---

### Post by kidders on 2006-10-07
Hi there,

It's not really the case that this is something that needs "fixing".

To be fully functional, ethereal needs root access to your system. No doubt, that fact is the single biggest contributor to ethereal's massive list of security vulnerabilities, but imo tweaking your system to let it run as a normal user would be far, far worse!

**Edit:** Sorry... I was too slow! Hehe.

---

### Post by styracosaurus on 2006-10-07
Okay. I guess that was my other question, is it bad to run it as root? But you answered that, it's not as bad as the alternative.

Thanks again!

---

### Post by kidders on 2006-10-07
I may be wrong, but imo running ethereal as root isn't so bad, provided nobody you don't trust is logged into your system at the same time.

Having said that, try not to develop a habit of overcoming permissions-related issues by running things as the superuser! Think of it as being a bit like running Windows XP with no firewall to stop bittorrent complaining. Hehe.

---

