---
title: "Server Virtualization"
date: 2008-09-05
forum: Fedora/RedHat and derivatives
---

### Post by john_sm on 2008-09-05
Hey Folks - We need your help. We were hoping, we could gain from your experience with implementing server virtualization. When should we be using Red Hat Virtualization, Citrix Virtualization, Xen Virtualization, Microsoft Virtualization, Oracle Virtualization and VMWare.  I will be very interested in learning from your first hand experience.  I will also like to know, under what situations is one virtualization preferred over the other.  - Thanks for your help

---

### Post by ilrudie on 2008-09-05
Xen and VMware are the best hardware virtualization vendors.  Oracle should stick to databases and Microsoft's products are always sub par (except their xbox and xbox related products).  

Xen owns Citrix.  Don't be mistaken though the product lines do different things.  Xen calls the Citrix Presentation Server "application virtualization" but you can still think of it as terminal services.  It has many nice features vanilla TS doesn't.

I don't know anything about Red Hat Virtualization but it seems to be pretty far from their core competency so I'd still probably say Xen or VMware for virtualizing hardware.

---

### Post by dca on 2008-09-08
In the mean time until things change and others catch up, in most of the shops I've been in VMWare has been the defacto standard.  Again, now that Citrix owns Xen, Sun owns VirtualBox, VMWare has new CEO, etc, etc things can change.
 
You'd be better off researching the differences in technology each solution uses in order to get to virtualization.  Some are kernel-level, some software/API (or whatever) level, some are direct-connect to hardware solutions.
 
... not to mention, not that this is a jab at MS but out of all the data centers I've been to in the past year or so, I never seen one that ran MS' hypervisor solution w/ Linux vms...  It's always been Linux w/ MS Server vms...  Who knows maybe their new vm which I hear is cheap may help them out but if I had to recommend.......

---

