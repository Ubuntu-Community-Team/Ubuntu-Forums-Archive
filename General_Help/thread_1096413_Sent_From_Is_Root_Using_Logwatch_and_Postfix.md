---
title: "Sent From Is Root Using Logwatch and Postfix"
date: 2009-03-14
forum: General Help
---

### Post by jaa546o on 2009-03-14
Hello all,

I've got Ubuntu 8.10 with Logwatch and Postfix installed from the Synaptics Package Manager. My question is on the outgoing Logwatch emails, how can I get the "Received From" address that I receive in my external email account to be "Logwatch@mydomain" instead of "root@mydomain".

Currently /usr/share/logwatch/default.conf/Logwatch.conf is configured with the default settings "Sent From = Logwatch" and the "Send To= root". The /etc/aliases file redirects the emails to my external email account. I have another system running Fedora Core 10 with Postfix and it sends Logwatch emails from "Logwatch@mydomain". I've checked the main.cf files for both systems and didn't see any obvious differences. Would appreciate any enlightment that anyone has to offer.

---

### Post by dcstar on 2009-03-15
> **jaa546o said:**
> Hello all,

I've got Ubuntu 8.10 with Logwatch and Postfix installed from the Synaptics Package Manager. My question is on the outgoing Logwatch emails, how can I get the "Received From" address that I receive in my external email account to be "Logwatch@mydomain" instead of "root@mydomain".

Currently /usr/share/logwatch/default.conf/Logwatch.conf is configured with the default settings "Sent From = Logwatch" and the "Send To= root". The /etc/aliases file redirects the emails to my external email account. I have another system running Fedora Core 10 with Postfix and it sends Logwatch emails from "Logwatch@mydomain". I've checked the main.cf files for both systems and didn't see any obvious differences. Would appreciate any enlightment that anyone has to offer.

Why not just make a "Logwatch" account and send the mail to that (redirected via alias)?

---

### Post by jaa546o on 2009-03-16
Good point. I'll give that a try.
Thanks

---

