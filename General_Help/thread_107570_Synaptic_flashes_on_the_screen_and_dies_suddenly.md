---
title: "Synaptic flashes on the screen and dies suddenly"
date: 2005-12-23
forum: General Help
---

### Post by djacobs on 2005-12-23
I ran my upgrades this morning (it was the new kernel) and rebooted. The upgrade reminder appeared again, but not synaptic only flashes on the screen for a second and then disappears. These messages appear in the syslog (and in messages)
djacobs@djacobs:/var/log$ Dec 23 11:22:43 djacobs gconfd (root-7958): starting (version 2.12.0), pid 7958 user 'root'
Dec 23 11:22:43 djacobs gconfd (root-7958): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Dec 23 11:22:43 djacobs gconfd (root-7958): Resolved address "xml:readonly:/usr/share/gconf/local.mandatory" to a read-only configuration source at position 1
Dec 23 11:22:43 djacobs gconfd (root-7958): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 2
Dec 23 11:22:43 djacobs gconfd (root-7958): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 3
Dec 23 11:22:43 djacobs gconfd (root-7958): Resolved address "xml:readonly:/usr/share/gconf/local.defaults" to a read-only configuration source at position 4
Dec 23 11:22:43 djacobs gconfd (root-7958): Resolved address "xml:readonly:/usr/share/gconf/cdd.defaults" to a read-only configuration source at position 5
Dec 23 11:22:43 djacobs gconfd (root-7958): Resolved address "xml:readonly:/usr/share/gconf/debian.defaults" to a read-only configuration source at position 6
Dec 23 11:22:43 djacobs gconfd (root-7958): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 7



Interestingly, if I run dpkg or aptitude, and THEN try and run synaptic, I get the expected behavior (which is just a message about the file being locked). 

Thanks
David

---

