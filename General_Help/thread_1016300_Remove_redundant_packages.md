---
title: "Remove redundant packages"
date: 2008-12-19
forum: General Help
---

### Post by PeterJCLaw on 2008-12-19
Hi,

I've just upgraded a desktop from 8.04.1 Hardy to 8.10 Intrepid and unfortunately I managed to crash the computer about half way through - the upgrade was complete but the cleanup was not.

This also caused me to wonder if a similar cleanup (in particular the redundant package removal part) was available somewhere other in Ubuntu other than in this installer?

Peter

---

### Post by mssever on 2008-12-19
> **PeterJCLaw said:**
> Hi,

I've just upgraded a desktop from 8.04.1 Hardy to 8.10 Intrepid and unfortunately I managed to crash the computer about half way through - the upgrade was complete but the cleanup was not.

This also caused me to wonder if a similar cleanup (in particular the redundant package removal part) was available somewhere other in Ubuntu other than in this installer?

Peter
If you use the command line version of aptitude to install and remove software, then it will offer to remove anything that's been marked as auto-installed. However, I suspect that the particular list that the upgrade tool gave is lost for good.

---

### Post by PeterJCLaw on 2009-03-21
"sudo apt-get autoremove"

[http://ubuntuforums.org/showthread.php?t=996053](http://ubuntuforums.org/showthread.php?t=996053)

---

