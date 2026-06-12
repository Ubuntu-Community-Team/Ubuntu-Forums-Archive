---
title: "root not getting emails"
date: 2010-06-19
forum: Desktop Environments
---

### Post by dave37 on 2010-06-19
Using Lucid, did some tinkering to try and forward root emails to an external address, didn't work, but now I discover that root isn't getting any emails.  If I use mutt to check for emails there are none any more.

After using system lock viewer I can see that postfix is trying to send the mail to [email]myusername@externalemailaddress.com[/email] instead of myusername@localhost.

Where do I define the localhost email address as that is what I must have messed up?

Solved: figured it out, issued command sudo dpkg-reconfigure exim4-config
and changed the email address to localhost in there and it's now working.

---

