---
title: "Rescue Windows with Ubuntu?"
date: 2009-05-07
forum: General Help
---

### Post by jago25_98 on 2009-05-07
I had a virus on Windows recently,
 so I rebooted into Ubuntu and ran $clamscan instead of trying to use windows to fix it. It worked well.

Is there anything else I can use to fix windows problems like this?

We have a slow windows box here (runs for about 10mins then freezes, don't think it's overheat).

There's usually safe mode available but I'd prefer to fix it with linux if possible. 

In fact, are there any tools that automate fixing Windows machine with these sorts of problems?

---

### Post by salvachn on 2009-05-07
Goto these folders from Windows:
C:\WINDOWS\system32
C:\Documents and Settings\username\<all folders here>
Look for dll and exe files that do not have any description, then google their names, if they are malicious, make a note of those files. Then disable them from startup using start->run->msconfig.
Then get into ubuntu, delete these files.

---

### Post by stinger30au on 2009-05-07
google on   ultimate boot cd for windows   make one of these and use the reocery tools as well  there is a number of antivirus tools etc to get rid of "nasties"

---

