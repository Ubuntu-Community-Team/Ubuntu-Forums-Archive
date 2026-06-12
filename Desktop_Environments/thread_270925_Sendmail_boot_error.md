---
title: "Sendmail boot error"
date: 2006-10-03
forum: Desktop Environments
---

### Post by RudolfMDLT on 2006-10-03
Hi there,

I've been strugeling to fix this error at startup:

[PHP]cannot remove /etc/mail/sendmail.cf :read only file system
Updating Autehntication
/usr/share/sendmail/update_auth : line 98 : cannot create temp file for here

Creating  /etc/mail/relay
Optional file

You should Issue "/etc/init.d/sendmail reload"  [/PHP]

This occurs in the orange Ubuntu load screen when it starts loading basic networking...


Could somone please tell what send mail is and what it does? I can restart the service in KDE but I would like to fix this error. 


Thanks,

Rudolf

---

### Post by kerry_s on 2006-10-07
Can you give any more info, like what exactly is being started. Try looking at your .xsession-errors for a clue(that's a hidden file in your home). I'm running a minimal kde install and don't have anything like that. Maybe even check in /var/log and see if there's a clue.

---

### Post by Anduu on 2006-10-07
This is a very old issue with sendmail.

From what I have been told sendmail is now an antiquated system and is not really supported anymore.It is also known to not be very secure these days.

I highly recommend switching to Postfix as it has all the functionallity as sendmail and is backwards compatible with systems that use sendmail.It sets up its own 'virtual' sendmail system complete with binaries so that apps that require sendmail will still function.

Now if you are adverse to trying something new there is a fix...however I am at a loss as to where it is.It is here in the forums somewhere...sorry i couldn't be more help.

---

### Post by RudolfMDLT on 2006-10-07
kerry_s and Anduu, Thanks! If sendmail is not supported anymore and considdered worthless, where do I remove it from the startup script to stop this error from being generated?

---

### Post by Anduu on 2006-10-07
It is as simple as installing Postfix or another mail system.Sendmail will be uninstalled so as not to conflict with the new mail system.

---

### Post by RudolfMDLT on 2006-10-08
Thank you very much!

---

