---
title: "Spam Filter with Evolution not working"
date: 2005-10-25
forum: Desktop Environments
---

### Post by djjuice on 2005-10-25
To compliment another thread..,
Several users including myself have done a fresh install of Breezy. Configured Evo and have installed spamassian ( I also installed spambayes) but even so with the junk rule enabled spam is not filtered. Did anyone get luck with the spam filter? Thanks!

---

### Post by RikBlankestijn on 2005-11-04
Hi, it appears that you have to set an option in /etc/default/spamassassin ENABLED=1 (which is by default ENABLED=0).
See this thread: [http://www.ubuntuforums.org/showthread.php?t=40858](http://www.ubuntuforums.org/showthread.php?t=40858)
I've just enabled it myself one minute ago so I can't really tell you it will work correctly now.

---

