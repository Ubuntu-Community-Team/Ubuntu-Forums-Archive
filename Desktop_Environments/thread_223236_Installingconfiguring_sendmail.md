---
title: "Installing/configuring sendmail"
date: 2006-07-26
forum: Desktop Environments
---

### Post by sutterp on 2006-07-26
I am relatively new to ubuntu but quite familiar with other distros. I am in the course of converting several SuSE Linux desktop machines to ubuntu. All these machines need to run sendmail (not postfix or exim).

I just installed sendmail on the first of them and am trying to go through the configuration procedure sendmailconfig. After the dialogue phase finishes and I have answered all the questions, this is what I get:

> Creating /etc/mail/sendmail.cf...
*** ERROR: FEATURE() should be before MAILER()
*** ERROR: FEATURE() should be before MAILER()
*** MAILER(`local') must appear after FEATURE(`allmasquerade')*** ERROR: FEATURE() should be befo re MAILER()
*** MAILER(`local') must appear after FEATURE(`always_add_domain')*** ERROR: FEATURE() should be before MAILER()
*** ERROR: FEATURE() should be before MAILER()
*** ERROR: MAILER(local) already included
*** ERROR: MAILER(smtp) already included

The initial 2 questions I answered as follows:
> Configure sendmail with the existing /etc/mail/sendmail.conf? [Y]Y

Configure sendmail with the existing /etc/mail/sendmail.mc? [Y]N
because I want to start from scratch and assume that the sendmail.conf that was installed is useable.

What goes wrong?

Thanks

Peter

---

### Post by cilynx on 2006-07-26
I know this is absolutely not the answer that you're looking for, but why are you set on sendmail?  Sendmail is pretty well published as the largest security hole in all of *NIX.  I don't know of anyone still running sendmail on purpose.  System migration time is a great time to move over to a more configurable and stable system.  My personal recommendation is qmail.  Yes, DJB is an ***, but qmail is a great piece of kit.

All that aside, I understand that at times for political reasons or due to massive custom software, you have to stick with old, insecure kit.  

In order to get up and running, we're going to need a little more info on what you're actually trying to do.

---

### Post by sutterp on 2006-07-27
> **cilynx said:**
> 
All that aside, I understand that at times for political reasons or due to massive custom software, you have to stick with old, insecure kit.  

In order to get up and running, we're going to need a little more info on what you're actually trying to do.

Thanks, cilynx

Ok, I will consider alternatives to sendmail provided that:

It is easy and quick to install (the sendmail setup on ubuntu seems to be broken) and configure, and meets the following requirement:

1. There are several (many, many) bash and php scripts running on the workstations that report exceptions via mailx to an external email address. These scripts, although written for a SuSE Linux system, work as they are and we don't want to change them, dont' fix what ain't broken).

2. The internet setup is a bit peculiar.

2.1 We are connected via ADSL and have a dynamic IP address which is listed in dnsrbl, so we can not send out the mail directly, as the receiving systems reject all messages that are dnsrbl listed as spam.

2.2 We can not use our ISP's mail server for outgoing mail, because they run a spam filter and almost all generated messages are trapped.

2.3 We use a third party service for our mail delegation, and this we use as our smtp and pop server. The workstations connect to it using evolution or kmail for both outgoing and incoming mails. The smtp server, of course, will not accept un-authenticated connections, i.e. for relaying we have to authenticate. The mechanism is by plain text authentication, no encryption.

I could not find any way to configure mailx to use an authenticated upstream smtp server, which is the reason for sendmail running on all workstations.

Peter

---

