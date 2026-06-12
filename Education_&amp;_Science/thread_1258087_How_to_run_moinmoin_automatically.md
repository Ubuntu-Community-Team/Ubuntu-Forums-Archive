---
title: "How to run moinmoin automatically?"
date: 2009-09-04
forum: Education &amp; Science
---

### Post by raminaghrobis on 2009-09-04
Hi, I'm using a wiki software called moinmoin as a desktop wiki, and I currently have to run "python wikiserver.py" from the folder wikiserver.py is in each time I start my PC, in order to use the wiki. Is there some way for this to be done automatically?

P.S. I'm not sure this post should be here, but I couldn't find anywhere else...

---

### Post by PGScooter on 2009-09-05
is this what you're looking for? system>preferences>startup applications

---

### Post by tgalati4 on 2009-09-06
Or add it to /etc/rc.local

---

### Post by raminaghrobis on 2009-09-06
I just add "python /home/username/moin/wikiserver.py" in the rc.local file? Does it go before or after the "exit 0" line?

---

### Post by tgalati4 on 2009-09-07
Before.  The exit 0 line means "Exit this script with error status 0, which means no errors."  If there is an error in your script, the script would exit with an error status of 1, but that would interfere with boot up.  This way, regardless of what happens inside that script, it will exit with no errors (even if there are errors) and boot will try to continue normally.

Without "exit 0" you get unceremoniously dropped to a command line:

Script rc.local exited with and error status of 1:

root>

So put your local scripts before the exit 0 in /etc/rc.local.

---

