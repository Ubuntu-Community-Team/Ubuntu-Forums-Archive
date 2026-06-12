---
title: "Broken Packages"
date: 2009-06-21
forum: General Help
---

### Post by AgentZ86 on 2009-06-21
Hi

I see in synaptic manager there is a link to click Broken Packages ?

What does this do and how can you tell if there is any Broken Packages ?

Also if there is any how does one fix them ?

Please advise
Thanks

---

### Post by james.brantley on 2009-06-21
> **AgentZ86 said:**
> Hi

I see in synaptic manager there is a link to click Broken Packages ?

What does this do and how can you tell if there is any Broken Packages ?

Also if there is any how does one fix them ?

Please advise
Thanks

[SIZE=3]"[COLOR=Red]apt-get -f install[/COLOR]" or "[COLOR=Red]dpkg --configure -a[/COLOR]" should try to fix broken packages. (run as sudo)
[/SIZE]

---

