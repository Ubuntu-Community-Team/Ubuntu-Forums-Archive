---
title: "No /bin/arch in Ubuntu ~ Deprecated"
date: 2009-02-26
forum: General Help
---

### Post by Xama on 2009-02-26
Trying to install certain applications which use install scripts (like Xilinx ISE 10.1 ) under Ubuntu, will fail because there is no /bin/arch. 

Annoyingly when things are deprecated scripts break. Thus the fix is to create /bin/arch as bash script which simply does.

uname -m

#Goodbye

---

