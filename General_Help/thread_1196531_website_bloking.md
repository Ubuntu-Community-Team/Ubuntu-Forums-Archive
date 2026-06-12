---
title: "website bloking"
date: 2009-06-25
forum: General Help
---

### Post by ramana1432 on 2009-06-25
i want to know how to block the websites in ubuntu..Is any software is required for that.Please help mee...


thanks and regarding
ramana rao

---

### Post by snek on 2009-06-25
There are various ways of doing this:
- Setup Squid
- Block them using IPTables
- Configure your computer/router to use OpenDNS and configure the blocking there (recommended, will work for all pc's in your network, I use it at work)
- Install a Firefox addon which blocks the sites
- Edit /etc/hosts to point the domain to localhost

I don't have time to explain these things but I'm sure you can find tutorials somewhere ;)

---

### Post by Barriehie on 2009-06-26
I use squid and it works very well for me.  I've setup a cron job to download a 'blacklist' once a week and remove duplicate entries and then restart squid so the new file is in use.  I've also incorporated my own blacklist so that as I browse I can add advertisers that aren't in the downloaded list.

Can help if you like.

Barrie

---

### Post by billgoldberg on 2009-06-26
/etc/hosts should do fine.

---

