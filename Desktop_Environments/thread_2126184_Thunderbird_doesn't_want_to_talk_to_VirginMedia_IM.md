---
title: "Thunderbird: doesn't want to talk to VirginMedia IMAP"
date: 2013-03-16
forum: Desktop Environments
---

### Post by XEtedBear on 2013-03-16
I'n using (well, not yet) Thunderbird 17.0.4 on Ubuntu 12.04. I'm trying to create an account on virginmedia using IMAP protocol. When I try to read mail the TB dialog asks for password to my mail server in the form <username>@imap.virginmedia.com.  I was expecting it to be in the form of <username>@virginmedia.com, for which I have been using the same password successfully for some time with a different email client in both POP and IMAP modes. Indeed the older client is still installed in Ubuntu and allows me to access my mail, using the same password.
 
Is the account name shown by Thunderbird correct or not?
 
If it is correct, why does it not accept my password (and, yes, I have checked that caps lock and scroll lock are not on!)?

---

### Post by XEtedBear on 2013-03-16
Ah, I seem to have stumbled on the correct, bizarre, form of email address which Thunderbird and VirginMedia IMAP will mutually accept: <username>@virginmedia.com@imap.virginmedia.com

This seems more than bizarre - it's perverse. I would never have thought of this and found it only by mistake. Neither the TB nor the VM documentation mention that this is the correct form of address - or at least one that works.

---

