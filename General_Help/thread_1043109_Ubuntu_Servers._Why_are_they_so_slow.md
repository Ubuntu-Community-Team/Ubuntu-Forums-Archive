---
title: "Ubuntu Servers. Why are they so slow?"
date: 2009-01-18
forum: General Help
---

### Post by C. Wizard on 2009-01-18
DSL service is down in my area and I've had to resort to using dial up.  Now, I know it is slow, I have no illusions about that, but I am able to download files at a relatively reasonable rate from various other sites, but trying to download updates from the Ubuntu servers is so painfully slow that I often give up after several hours of trying.

Just a short while ago I downloaded the most recent WINE update, that comes from their server, and it didn't take any longer than one would expect on a dial up connection.

BUT, try downloading almost anything from a Ubuntu server and the download rate is at full speed one moment and zero the next.  It can take, and I'm not exaggerating, more than 24 hours to down a file which shouldn't take more than 30 minutes if the speed would remain consistent.

Is there any way to improve the situation?

Thanks.

---

### Post by arctic on 2009-01-18
Try to define a different default-server, e.g. using the synaptic package manager.

---

### Post by C. Wizard on 2009-01-19
> **arctic said:**
> Try to define a different default-server, e.g. using the synaptic package manager.

Tried that and it took almost 9 hours to reload the file lists.

---

### Post by arctic on 2009-01-19
Then the problem is probably not directly related to the software mirrors themselves but your internet-connection. Maybe it has difficulties with the IPV6 protocol and/or your DNS servers. Check if your DNS server entries are okay and if IPV6 is disabled.

---

### Post by C. Wizard on 2009-01-20
> **arctic said:**
> Then the problem is probably not directly related to the software mirrors themselves but your internet-connection. Maybe it has difficulties with the IPV6 protocol and/or your DNS servers. Check if your DNS server entries are okay and if IPV6 is disabled.

That is all "Greek" to me. How can I change anything when I'm dialing out using KPPP?  IPV6 is what?
I don't have problems with other sites?
Now almost 14 hours since I started to download a 10 meg file, kdelibs5, that would have taken 30 minutes from any other site.

---

### Post by C. Wizard on 2009-01-20
OK, I've looked up IPV6. No wonder I haven't heard of it.

"In December 2008, despite celebrating its 10-year anniversary as a Standards Track protocol, IPv6 was only in its infancy in terms of general world-wide deployment. A recent study[1] by Google indicates that penetration is still less than one percent of Internet traffic in any country."

[http://en.wikipedia.org/wiki/IPv6](http://en.wikipedia.org/wiki/IPv6)

---

### Post by Seq on 2009-01-20
> **C. Wizard said:**
> DSL service is down in my area and I've had to resort to using dial up.

How long is it down for? I'd honestly just wait. You have a finite amount of bandwidth: use it for something more interesting than kdelibs ;)

---

