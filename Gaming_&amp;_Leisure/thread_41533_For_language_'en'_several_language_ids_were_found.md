---
title: "For language 'en' several language ids were found:"
date: 2005-06-13
forum: Gaming &amp; Leisure
---

### Post by Snipersnest on 2005-06-13
Anybody know how to fix this problem??

[b]For language 'en' several language ids were found:
en_US - 0409; en_GB - 0809; en_AU - 0C09; en_CA - 1009; en_NZ - 1409; en_IE - 1809; en_ZA - 1C09; en_JM - 2009; en_ - 2409; en_BZ - 2809; en_TT - 2C09;
Instead of using first in the list, suggest to define
your LANG environment variable like this: LANG=en_US
[/b]
Heres a list of things I've tried:

**sudo view /etc/enviroment **
-File Contents- LANGUAGE="en_US" LANG=en_US

**sudo dpkg-reconfigure locales**
basicly just edits the file I listed above...

I can't seem to get an answer on this from the TransGaming crew...No one seems to know how to fix this problem either.  When I first installed Cedega and Point2Play things worked fine...once I installed Wine so I could install some of my Windows based apps I started getting the error.  I removed the wine packages yet still I get the error. I reinstalled P2P/Cedega...no change. 

Any ideas?

---

### Post by Fizile on 2005-07-13
I'm having this same problem when attempting to install the game Natural selection, which is a hl1 mod for steam...

Doesnt seem like there is a fix for this from my forum search! I love ns!  Any help would be appreciated.  Cedega 4.3.2-1

---

### Post by Snipersnest on 2005-07-14
Yes I did get it fixed... Simply make sure that the enviroment file has what I listed above...then reboot your computer. Logging out doesn't do it.
 
It fixes the problems. Then once you've rebooted verify that the file didn't get changed.
 
Let me know if you can't get it and I'll help you out some more.

---

