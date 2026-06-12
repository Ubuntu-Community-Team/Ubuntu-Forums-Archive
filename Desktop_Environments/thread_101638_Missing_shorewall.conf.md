---
title: "Missing shorewall.conf"
date: 2005-12-10
forum: Desktop Environments
---

### Post by justin_p on 2005-12-10
I have a brand new 5.10 (which is by far the best distro I have used to date).  I have a standalone system and have been trying to configure shorwall.  In reading the documentation the setup is easy easy enough.  I did notice the notes to Debian users.  I set up my interfaces, policy, and rules.  But there is no shorewall.conf file in my computer.  I searched and nothing.  I have reinstalled the prog once, no luck.  Anyone have similar errors?  Or know how to address?  Thanks.

---

### Post by BrowneR on 2006-08-21
i too am also missing the shorewall.conf file which is supposed to be avaliable in the /usr/share/shorewall/default-config dir

---

### Post by sno on 2006-08-22
Its in de /etc/shorewall dir. 
And the modules are in the /usr/share/shorewall/default-config dir, cp them as well.
Then pick an sample netconfig from /usr/share/shorewall/'samplenetconfig' and extract the gz into the /etc/shorewall, edit as u like.
The docs on the webby are good, but dont forget to install the shorewall-doc pkg as well!!

---

