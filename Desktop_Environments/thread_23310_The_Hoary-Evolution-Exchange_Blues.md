---
title: "The Hoary-Evolution-Exchange Blues"
date: 2005-04-01
forum: Desktop Environments
---

### Post by eroux on 2005-04-01
Hi all,

I've installed Hoary onto my desktop machine and have run into a seemingly insurmountable problem.

The corporate I work for has standardised on different User names and Mailbox names. Evolution 2.2.x, however, seems to prefer the two to be the same, and if you cannot comply with that, then tough...

Does anyone know of any way of having different Usernames and Mailbox names in Evolution 2.2?

Thanks in advance,
Eugéne

---

### Post by eroux on 2005-04-11
[QUOTE=eroux]Hi all,
Does anyone know of any way of having different Usernames and Mailbox names in Evolution 2.2?
[/QUOTE]

Still nothing?

Chirp... Chirp...

Anyone?...

Chirp... Chirp...

Damn, I can't believe I'm the only one with this issue!

Eugéne

---

### Post by souki on 2005-04-11
[QUOTE=eroux]Still nothing?

Chirp... Chirp...

Anyone?...

Chirp... Chirp...

Damn, I can't believe I'm the only one with this issue!

Eugéne[/QUOTE]
 I'm not sure to understand your problem.

If you need to separate the emails by address:
set up a virtual folder with: Recipient is [email]account1@yourdomain.com[/email]
and an other one with: Recipient is [email]account2@yourdomain.com[/email]

If you need to switch from one account to an other when composing email, you can choose with the 'From:' combo

If you have an IMAP server, just set up your accounts, and subscribe to the folders

---

### Post by eroux on 2005-04-11
[QUOTE=souki]I'm not sure to understand your problem.
[/QUOTE]

The problem is that, if you are using the Exchange connector, the one used in Evo 2.2 expects your Windows Login name to be the same as your Mailbox. This is not always the case, and, since I just found this bugzilla [report](https://bugzilla.ubuntu.com/show_bug.cgi?id=8100) it does seem that I'm not alone in this.

What happens is that the connector will authenticate just fine, but will then abort when it doesn't find your mailbox. In my case, for instance, my login is something like rouxeu, but my mailbox (and consequently my email address) is eugene.roux@.... On login the connector tries to open the rouxeu mailbox, whis does not exist.

Older connectors had seperate entries for login and mailbox, so they worked just fine...

Regards,
Eugéne

---

### Post by eroux on 2005-04-11
[QUOTE=eroux]What happens is that the connector will authenticate just fine, but will then abort when it doesn't find your mailbox. In my case, for instance, my login is something like rouxeu, but my mailbox (and consequently my email address) is eugene.roux@.... On login the connector tries to open the rouxeu mailbox, whis does not exist.
[/QUOTE]

This has been fixed in the connector released to the APT repositories from CVS on 2005-04-05...

All seems to work fine now.

Regards,
Eugéne

---

