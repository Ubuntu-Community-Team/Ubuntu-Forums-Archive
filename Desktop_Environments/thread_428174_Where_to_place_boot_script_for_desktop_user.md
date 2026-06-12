---
title: "Where to place boot script for desktop user?"
date: 2007-04-30
forum: Desktop Environments
---

### Post by AbacusDev on 2007-04-30
Hello All-
Just got my 7.04/AMD system up last night and it's great.  Only one problem, where to place my custom boot script for a given desktop user (i.e. not  a system script, just one for a particular desktop user at Gnome's start)?
Cheers,
Tom R.

---

### Post by lcg on 2007-04-30
> **AbacusDev said:**
> Hello All-
Just got my 7.04/AMD system up last night and it's great.  Only one problem, where to place my custom boot script for a given desktop user (i.e. not  a system script, just one for a particular desktop user at Gnome's start)?
Cheers,
Tom R.

If it is a generic script, which could also be useful for other users, I would put it in /usr/bin/ (or if there are no other users on that box, I'd also put it there). If it is only of use for that one user, I'd place it in a (newly created) directory ~/bin/.

HTH,
Lars

---

### Post by AbacusDev on 2007-04-30
Thanks for your reply.  So, is my question clear to you?  I'd like the script to run automatically at X (desktop) startup.  How would the script in ~/bin know to start?  
Regards,
Tom R.

---

### Post by AnRa on 2007-04-30
System -> Preferences -> Sessions
 :)

---

### Post by lcg on 2007-05-01
> **AbacusDev said:**
> Thanks for your reply.  So, is my question clear to you?  I'd like the script to run automatically at X (desktop) startup.  How would the script in ~/bin know to start?  
Regards,
Tom R.
Your question was perfectly clear. You asked where to put the script, not how to make Gnome start it! ;)

But AnRa already answered that part, nothing left for me to do ...

Regards,
Lars

---

### Post by AbacusDev on 2007-05-01
Got it.  My question should have been stated more clearly.
Much thanks,
Tom R.

---

