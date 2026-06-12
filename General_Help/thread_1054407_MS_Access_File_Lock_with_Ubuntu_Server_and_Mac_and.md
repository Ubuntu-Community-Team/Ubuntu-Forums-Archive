---
title: "MS Access File Lock with Ubuntu Server and Mac and PC Clients"
date: 2009-01-29
forum: General Help
---

### Post by flax1905 on 2009-01-29
I recently had a problem of having a MS Access file lockups on my server. MS Access creates a *.ldb file with the same name as the data base file when opened by a client. By adding the following to the smb.conf file, the problem was solved.

  force group = workgroup
  create mask = 0770
  force create mode = 0770
  directory mask = 0770
  force directory mode = 0770
  directory security mask = 0770
  security mask = 0770
  force security mode = 0770
  force directory security mode = 0770

Initially, I just wrote the create mask and directory mask in the config file, only to find out the the permissions were still 
-wrxwr---- on the *.ldb file. Adding the force commands above solved the problem. The *.ldb file is now -wrxwrx---

---

