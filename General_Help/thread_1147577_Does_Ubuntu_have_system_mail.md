---
title: "Does Ubuntu have system mail?"
date: 2009-05-03
forum: General Help
---

### Post by davidpbrown on 2009-05-03
Other Linux systems seem to have system mail from cron jobs and the like. I've have some from ~Dapper but have seen no messages in the latest couple of incarnations of Ubuntu.

Has system mail been phased out; is it just the log files communicating to the sudo users?

---

### Post by ddrichardson on 2009-05-03
[http://ubuntuforums.org/showthread.php?t=7321](http://ubuntuforums.org/showthread.php?t=7321)

---

### Post by BslBryan on 2009-05-03
System mail still exists, and is located here:
```
/var/mail/account_name
```

Check [this]("https://help.ubuntu.com/9.04/installation-guide/powerpc/mail-setup.html") out for more information.

EDIT: ddrichardson beat me to it.  :P

---

### Post by davidpbrown on 2009-05-03
Thanks for the abc.

I know how to do that but having set it up last couple of installations then never received a mail. So, I'm wondering is it worth doing again.

Does mail happen only when there is a problem and is not getting any is a good sign?? Might there be a good use for it - asking for more reporting by the system for example?? Just trying to understand it better..

---

### Post by ddrichardson on 2009-05-03
> **BslBryan said:**
> EDIT: ddrichardson beat me to it.  :P
Totally bums me when that happens ;-)

---

### Post by davidpbrown on 2009-05-03
and thanks BslBryan.. I've not got to using an MTA directly. Not having ever seeing the /var/mail/account_name I've created it myself trying to catch something but still no mail, which I'm just thinking is odd.

---

### Post by BslBryan on 2009-05-03
> **ddrichardson said:**
> Totally bums me when that happens ;-)
+1 :)


> **davidpbrown said:**
> and thanks BslBryan.. I've not got to using an MTA directly. Not having ever seeing the /var/mail/account_name I've created it myself trying to catch something but still no mail, which I'm just thinking is odd.

You did replace "account_name" with the name of your account, right?  You probably did, but these things slip everyone's minds sometimes.  ;-)

---

### Post by davidpbrown on 2009-05-03
:lolflag:

I'm wondering if having cron jobs throw mail might be useful.. don't know if that's easy to do but not having any system mail makes me hesitate it's not working atm.

---

### Post by BslBryan on 2009-05-03
> **davidpbrown said:**
> :lolflag:

Thought so. :)

---

