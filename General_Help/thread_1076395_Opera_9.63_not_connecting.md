---
title: "Opera 9.63 not connecting"
date: 2009-02-21
forum: General Help
---

### Post by Faolan on 2009-02-21
Got a weird fault with Opera and/or my LAN. This fault has been verified on two systems and 3 versions of Ubuntu (7.04, 8.04 and 8.0) using the .deb file from Opera.

Firefox connects and views webpages with no issue and so does the update manager. 

There is no pages being loaded with Opera they just time out, localhost pages are fine. So I'm asking is there anything I need to be aware of with Ubuntu. One PC is using DHCP from my gateway and the other is using Static IP both are using different architectures. I would think it's something to do with my LAN but other PCs with Opera work fine (under varients of Windows).

---

### Post by Faolan on 2009-09-01
Resurrecting an old thread to advise on the resolution of the fault. Still using Hardy 8.04 and not tried this on newer distros yet.

Essentially the cause of Opera not connecting to the 'Net is that it's stalling due to IPV6, because my router doesn't support it (I presume) so I disabled this protocol.

Not the ideal solution, but if Vista, Windows 7 can support IPV6 and not stall Opera I can't see why Ubuntu will throw a fit over this.

---

### Post by gjoellee on 2009-09-01
Zombie Thread?!!

[IMG]http://www.scottsmind.com/cartoons/scottsmind/zombie.gif[/IMG]

---

### Post by Faolan on 2009-09-01
> **gjoellee said:**
> Zombie Thread?!!

There's always one :P

This also affected Opera 10, so that's why I updated this thread and I why resorted to disabling services. Flash now works perfectly in Opera, something that Firefox still can't get right.

---

