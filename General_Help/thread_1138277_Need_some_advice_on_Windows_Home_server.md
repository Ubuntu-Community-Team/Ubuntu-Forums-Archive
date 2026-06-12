---
title: "Need some advice on Windows Home server"
date: 2009-04-26
forum: General Help
---

### Post by waheedrafiq on 2009-04-26
Okay guy's I know I heard about this Windows Home server and seen a demo version of it on Microsoft site.

As I have Vowl not to use MS product is there alternative product to this OS that I can install on my bog standard PC

---

### Post by danwood76 on 2009-04-26
Well you could just run a samba server.
I assume that home server is just like a glorified NAS, it doesnt look (from the ms site) to do much else which samba is more than capable of.

You can use a simple free backup utility to backup all the data from your machines (we use back2zip at work in a similar setup)

If you are looking for more of a log in style server samba can be used as a Domain Controller (PDC) and samba 3 works well in this mode with XP and works ok in Vista.

---

### Post by oly on 2009-05-11
Well your options are to setup one yourself.

or try one of these projects which are in development as windows home server replacments.

[www.ubuntuservermanager.org](www.ubuntuservermanager.org) already does quite a lot
[www.satega.org](www.satega.org) quite early in developemnt

or use a more buisness oriented solution like ebox webmin freenas sme server.

---

### Post by mixmaster on 2009-05-11
> **danwood76 said:**
> Well you could just run a samba server.
I assume that home server is just like a glorified NAS, it doesnt look (from the ms site) to do much else which samba is more than capable of.

You can use a simple free backup utility to backup all the data from your machines (we use back2zip at work in a similar setup).
I've never used home server myself but I'm told that as a fileserver/backup system etc it is actually quite capable.  One of my workmates - generally a linux advocate and a very competent home sysadmin - swears by it as a turnkey solution in those areas.  He thinks it is probably the best OS M$ have released.

You can get the same functionality from a linux server but you may have to work at it.  I'm not sure how far advanced the Home Server replacement projects have advanced.

---

