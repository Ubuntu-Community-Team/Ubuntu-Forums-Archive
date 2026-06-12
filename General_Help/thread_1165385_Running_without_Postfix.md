---
title: "Running without Postfix"
date: 2009-05-20
forum: General Help
---

### Post by jdege on 2009-05-20
Keeping a mail server configured to be secure is a fair bit of work, given the way the attacks keep evolving.

We have a couple of Ubuntu boxes running as servers, connected to the net, and one of them seems to have been used as a mail relay.

Among the alternatives we've been considering is simply to not have a mail server running on the machine at all.  Unfortunately, this doesn't quite work.

We have no problem in sending mail from the machine, while Postfix is not running.  And there's no account on the machine we want to receive mail.  The only problem is the system-generated emails.  Alert messages going to root, cron output, etc.  We have .forwards established for root and the couple of non-root accounts that we are concerned with, but mail to these users doesn't forward off the machine unless Postfix is running.

Is there a way to either

1, configure the system so that .forwards work in redirecting mail off of the machine, when Postfix is not running, or

2. configure Postfix so that it will handle internal .forwards, but won't accept mail from anyone else?

Help would be appreciated.

---

### Post by dcstar on 2009-05-21
> **jdege said:**
> 
.........
2. configure Postfix so that it will handle internal .forwards, but won't accept mail from anyone else?

Help would be appreciated.

Postfix will only accept data from networks and for domains **you** clearly define in the main.cf file.

You can also reconfigure it to be an internal system only:

```
sudo dpkg-reconfigure postfix
```

If you don't want any incoming port 25 connections either block them with a firewall or change/disable the port.

---

