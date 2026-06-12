---
title: "Cannot update or add new programs"
date: 2009-03-17
forum: General Help
---

### Post by Ashin Sopaka on 2009-03-17
After running the Update Manager and trying to add a new program, the following message appears, for the first time (never had problems before!)

Any suggestions?

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report

Thank you.

---

### Post by mb_webguy on 2009-03-17
Open the terminal and enter the command "sudo dpkg --configure -a".

---

### Post by Ashin Sopaka on 2009-03-17
You know, I thought there was probably some complicated configuring that would have to be done after entering that command, which is why I didn't do it. 

Thanks so much, it worked (of course!)

---

