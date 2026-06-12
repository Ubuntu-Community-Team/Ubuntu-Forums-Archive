---
title: "akonadi_nepomuk_contact_feeder and related akonadi KDEPIM functions lock system"
date: 2010-11-03
forum: Desktop Environments
---

### Post by Hellmark on 2010-11-03
After a recent update of KDElibs, I started having it where shortly after logging in, my system resources will gradually just get used to the point that the entire system stops responding. I've had it where I dropped out of X using Control alt F1, and begin to login only to have it eventually report that the login failed due to time out, because I don't get the password prompt to appear within 60 seconds. 

Now, I've found out that if I kill akonadi_nepomuk_contact_feeder, akonadi_vcard_resource, akonadi_maildir_resource, akonadi_maildispatcher_agent, and akonadi_ical_resource that the computer proceeds like normal afterwards. It is most noticed when akonadi_nepomuk_contact_feeder is killed. All of these are part of the kdepim-runtime package. I do not use any of the KDE PIM apps (Kmail, kwallet, kaddressbook, etc) or nepomuk (by default, nepomuk was not enabled on my system, and I don't care to use it in the first place).  Unfortunately, I cannot remove this package due to how the dependencies are. When I've tried, it wanted to remove everything KDE, plus other nonrelated things such as apport. Just went through in synaptic, and marked kdepim-runtime to be removed, and if I marked anything else to be reinstalled, or just unmarked it, kdepim-runtime got unmarked.

What can I do to fix this problem?

---

