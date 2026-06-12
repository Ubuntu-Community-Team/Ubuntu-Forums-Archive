---
title: "Problem with update manager"
date: 2009-04-09
forum: General Help
---

### Post by eliasalucard on 2009-04-09
When I try to install updates I always get this message:

W: Failed to fetch [http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu/intrepid/miro-data_2.0.4-0pcf1_all.deb](http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu/intrepid/miro-data_2.0.4-0pcf1_all.deb)
  **Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)**


W: Failed to fetch [http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu/intrepid/miro_2.0.4-0pcf1_i386.deb](http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu/intrepid/miro_2.0.4-0pcf1_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


What do I do?

---

### Post by Wayne_V on 2009-04-09
You get that error when you run 'sudo apt-get update'?

Can you post /etc/apt/sources.list ?

---

### Post by taurus on 2009-04-09
You need to close down update manager first.  Then, go into System -> Administration -> Software Sources and use another server.

---

