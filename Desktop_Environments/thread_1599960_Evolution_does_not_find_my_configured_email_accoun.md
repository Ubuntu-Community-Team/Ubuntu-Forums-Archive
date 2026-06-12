---
title: "Evolution does not find my configured email account anymore"
date: 2010-10-18
forum: Desktop Environments
---

### Post by raider-G on 2010-10-18
Hi,

I had configured a gmail account in evolution and used it successfully until recently when after a restart evolution asks me again to configure an email (Evolution setup assistant wizard) again.

I already have my email configured but something must be preventing evolution to find my email account. What can I do to recover all that ? Any suggestions that may help are appreciated

PS: My .evolution/mail folder still has all the data for example (got there some hundreds MB still). and I also have there other folders: addressbook, calendar..etc

---

### Post by TNT1 on 2010-10-18
My evo just did that to me... I rebooted and it was fine. When last did you update? Maybe something there is bugging us?

---

### Post by raider-G on 2010-10-18
> **TNT1 said:**
> My evo just did that to me... I rebooted and it was fine. When last did you update? Maybe something there is bugging us?

I am quite up to date. I have 2.28.3-0ubuntu package for evolution, on Ubuntu 10.04
Is there a way to see some logs related to evolution that might help. starting from console seems not be be of too much help:

~$ evolution
RSS Plugin enabled (evolution 2.28, evolution-rss 0.2.0)
** (evolution:8473): DEBUG: mailto URL command: evolution %s
** (evolution:8473): DEBUG: mailto URL program: evolution

---

### Post by TNT1 on 2010-10-18
[http://projects.gnome.org/evolution/bugs.shtml](http://projects.gnome.org/evolution/bugs.shtml)

---

### Post by raider-G on 2010-10-18
Run evolution with logging like this: CAMEL_DEBUG=all evolution >& evo.log
I pasted the output to pastebin:
[http://paste.ubuntu.com/515806/](http://paste.ubuntu.com/515806/)

The logs are until the evolution account wizard opens (by the time it should already see that I had a gmail account there). Couldn't find myself anything out of order, but on the other hand I don't know how to read those logs.

---

### Post by raider-G on 2010-10-18
> **TNT1 said:**
> [http://projects.gnome.org/evolution/bugs.shtml](http://projects.gnome.org/evolution/bugs.shtml)

Just wanted to let everybody know I've also opened a bug: [https://bugzilla.gnome.org/show_bug.cgi?id=632496](https://bugzilla.gnome.org/show_bug.cgi?id=632496) ( cross-referenced to this thread also from the bug description). I guess this should be all-right.

---

### Post by raider-G on 2010-10-19
> **raider-G said:**
> Just wanted to let everybody know I've also opened a bug: [https://bugzilla.gnome.org/show_bug.cgi?id=632496](https://bugzilla.gnome.org/show_bug.cgi?id=632496) ( cross-referenced to this thread also from the bug description). I guess this should be all-right.

The bug was closed as INVALID. It seems that was not enough information to trace the cause of my problem. From the point of view of evolution my email account didn't exist so I had to recreate my IMAP gmail account (email address). I guess it's a good idea to back up your email waiting for this to happen :-)

See
[http://live.gnome.org/Evolution/FAQ#How_can_I_completely_backup_evolution.3F](http://live.gnome.org/Evolution/FAQ#How_can_I_completely_backup_evolution.3F)

But I already had my ~/.evolution folder OK - in great lines at least(just that my email account wasn't seen by evolution) and was able to move my data back again after recreating my IMAP mail. Make sure you back up .evolution folder as recreating your email address wipes all that data (including contacts, possibly calendar)

---

### Post by raider-G on 2010-10-21
I recreated my IMAP gmail account and observed issues when trying to send a new email. They remain in Outbox and an error is displayed:


MAIL FROM command failed: Authentication Required. Learn more at                              
[http://mail.google.com/support/bin/answer.py?answer=14257](http://mail.google.com/support/bin/answer.py?answer=14257) g8sm839851bkg.23

MAIL FROM command failed: Authentication Required. Learn more at                              
[http://mail.google.com/support/bin/answer.py?answer=14257](http://mail.google.com/support/bin/answer.py?answer=14257) f21sm465731bkf.0

---

### Post by raider-G on 2010-10-21
[QUOTE=raider-G;10004274]I recreated my IMAP gmail account and observed issues when trying to send a new email. They remain in Outbox and an error is displayed:

I've forgot to mark "server required authentication" when creating the mail account.

---

