---
title: "Evolution and LDAP"
date: 2005-09-18
forum: Desktop Environments
---

### Post by rjr1049 on 2005-09-18
Maybe I am learning-disabled but I can't get Evolution to search an LDAP directory.  It works fine in T-Bird.  I have seen some reports on the web through a Google search that Evolution can't do this but Novell claims, on its web site, that it can.  The reports out there claiming that it had problems aren't enough to convince me that this is the case since it seems so strabge that Evolution can't do something as basic as this and there are so few of these claims that I found.  Can anybody enlighten me?  Thanks in advance for your response. :)

---

### Post by ahood on 2005-10-25
I have the same problem with Evolution (2.4.1) in Breezy. For some reason, Evolution appears to make the connection to an LDAP directory, but refuses to search it and display contacts. This works in Mozilla Thunderbird, but not Evolution.

:sad: 

Dr. Hood

---

### Post by Petrush on 2005-11-01
Same problem here, Can't get evolution to show contacts on the server. Works fine in thunderbird and luma, so server seems to be properly configured.

Is this a bug or a non-feature? I would assume it's a bug? It's a pity since for a workgroup this is a very usable thing..

Regards

---

### Post by Petrush on 2005-11-01
This is really an issue for us, is it somehow possible to downgrade to a version that works better (we have major IMAP and LDAP problems with 2.4 breezy)?

---

### Post by daleki on 2006-11-04
In my case LDAP started working when I specified an 'ou' in the 'Search base' field for evolution.  I did not have to do this in Thunderbird, just set dc there.

Click on the LDAP server
Right click and choose properties
Click the details tab
Set 'Search base' to match your environment:
```
ou=personal,dc=homedns,dc=org
```

---

