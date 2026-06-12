---
title: "synaptic package manager problem"
date: 2009-02-23
forum: General Help
---

### Post by salman203 on 2009-02-23
when i try to launch Synaptic package Manager , it fails to launch with the following error message

> [B][SIZE="3"][COLOR="Navy"]An error ocured
The following details are provided:[/COLOR][/SIZE][/B]
E: dpkg was interrupted, you must manually run
'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report. 


please, can any one guide me how to solve this problem. i m new into ubuntu

---

### Post by mb_webguy on 2009-02-23
Open the terminal and type "sudo dpkg --configure -a".

---

### Post by salman203 on 2009-02-23
thanks a lot, it solved the problem

---

