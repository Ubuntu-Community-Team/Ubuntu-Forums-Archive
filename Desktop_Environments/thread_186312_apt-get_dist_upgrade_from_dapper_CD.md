---
title: "apt-get dist upgrade from dapper CD?"
date: 2006-06-01
forum: Desktop Environments
---

### Post by digitalkarabao on 2006-06-01
Question guys. Can I add the CD in my sources.list and run apt-get dist upgrade to upgrade from Breezy to Dapper?

---

### Post by 5-HT on 2006-06-01
You can do that with the 'alternate CD' (what used to be the installation cd), but not the live/installer CD.

Hope that helps.

---

### Post by digitalkarabao on 2006-06-02
awww. bad news for me. so the only way of upgrading to dapper is by apt-get dist upgrade over a broadband connection?

---

### Post by rcarring on 2006-06-02
You can download the alternate cd iso, burn it, add it to the list of repos. Drop all the Breezy repos, and then do (in synaptic) Mark All Upgrades and it should do the upgrade.

---

### Post by digitalkarabao on 2006-06-02
Doing this did not upgrade my 5.10 to 6.06.  Only a few packages were updated.  Any idea if this is possible? Or i really have to either do a apt-get dist-upgrade connected via broadband or wipe out my HD and install a clean installation of Dapper.

---

