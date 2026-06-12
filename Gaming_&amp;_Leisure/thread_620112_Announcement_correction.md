---
title: "Announcement correction"
date: 2007-11-22
forum: Gaming &amp; Leisure
---

### Post by dmn_clown on 2007-11-22
You do not need to hard reset to exit a fork bomb:

```
while (sleep 100 &!) do; done

```

Z-shell code that kills the bomb fairly quickly.

Rather than trying to scare the living crap out of new and inexperienced users, why not point them in the proper direction so that they learn how to easily prevent these sorts of "attacks"?

For example, the effects of a fork bomb can be completely mitigated by limiting the number of processes that can be run at any one time by users and root. /etc/security/limits.conf exists for a reason, learn what it's use is and how to properly use it for your particular situation.

Also, you don't necessarily have to trust the person who's code you are executing (namely in the lines of shell scripts), you just have to know what the script does, most scripting languages are very well documented, Google is your friend here, as are many wonderful books that have been published on the subject.  Learning something new is wonderful :)

---

