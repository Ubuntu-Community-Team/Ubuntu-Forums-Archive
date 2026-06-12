---
title: "squid - ERROR Running Copy"
date: 2008-12-29
forum: General Help
---

### Post by tgilber1 on 2008-12-29
When starting up and shutting down, Ubuntu - Intrepid - 8.10 kept getting squid errors, "ERROR - No Running Copy."  I isolated the error to the bind9 daemon (DNS - named).  Bind9 reloads squid when starting or shutting down.  In this case, it was trying to reload squid after it has been shut down, hence the "No Running Copy" error.

To fix the problem, I rearranged my squid init script to start up before bind9 and shut down after bind9.

Ubuntu provides two easy ways to reconfigure init.d scripts.

1.  bum [boot-up manaager] - sudo apt-get install bum

or

2.  update-rc.d

       a.  sudo update-rc.d -f squid remove # to remove existing rc.d links
       b.  sudo update-rc.d squid defaults 14 28 # 14/28 represent start & stop

---

