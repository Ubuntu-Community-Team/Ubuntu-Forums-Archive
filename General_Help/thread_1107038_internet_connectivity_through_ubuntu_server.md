---
title: "internet connectivity through ubuntu server"
date: 2009-03-26
forum: General Help
---

### Post by speedy_pg on 2009-03-26
I am running ubuntu server through virtul box on an xp machine. how do get internet conenctivity through ubuntu?

i want to be able to run apt-install commands etc

---

### Post by decoherence on 2009-03-26
> **speedy_pg said:**
> I am running ubuntu server through virtul box on an xp machine. how do get internet conenctivity through ubuntu?

i want to be able to run apt-install commands etc

What kind of networking is the virtual machine set to use? NAT? Host Interface?

I haven't set up VirtualBox on XP, but assuming you're using at least version 2.1, try enabling "Host Interface" in the virtual machine's settings. Then boot Ubuntu and configure it for the network as if it was a real computer.

NAT should also work but I haven't bothered with it.

---

