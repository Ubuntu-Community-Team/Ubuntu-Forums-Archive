---
title: "Postfix issue after 8.10 upgrade"
date: 2009-03-04
forum: General Help
---

### Post by lordbah on 2009-03-04
zen.spamhaus.org was working fine with postfix while I was on Ubuntu 8.04 on my home server. Over the weekend I upgraded to 8.10. The log shows that it is still trying to use zen.spamhaus.org, but **every **query fails. All queries on bl.spamcop.net are failing as well. So basically no external email is getting in.

I can't think what I might have forgotten to do. These turn into simple DNS lookups, right? I don't have any problem with DNS in general. I can point my web browser anywhere and it works, I can grab packages with Synaptic, Pidgin works fine.

Here's an example of a private message sent to myself on ubuntuforums.org, turned into an email to me at home.

Mar  4 13:25:20 penguin postfix/smtpd[29652]: connect from unknown[91.189.94.170]
Mar  4 13:25:20 penguin postfix/smtpd[29652]: warning: 170.94.189.91.bl.spamcop.net: RBL lookup error: Host or domain name not found. Name service error for name=170.94.189.91.bl.spamcop.net type=A: Host not found, try again
Mar  4 13:25:20 penguin postfix/smtpd[29652]: NOQUEUE: reject: RCPT from unknown
[91.189.94.170]: 450 4.7.1 <bilberry.canonical.com>: Helo command rejected: Host not found; from=<www-data@bilberry.canonical.com> to=<XXXXX@XXXXXX.com> proto=ESMTP helo=<bilberry.canonical.com>
Mar  4 13:25:20 penguin postfix/smtpd[29652]: disconnect from unknown[91.189.94.170]

(Log modified with 'X's to hide my real email address)

From my work computer (Windows XP), if I query 170.94.189.91.bl.spamcop.net in nslookup I get back "Non-existent domain". That means "it's not on any evildoer lists, you should accept mail from this site", right? So why has postfix remembered that it's supposed to consult this list, but apparently forgotten that not-found means the site is okay?

Or am I totally misunderstanding something?

---

