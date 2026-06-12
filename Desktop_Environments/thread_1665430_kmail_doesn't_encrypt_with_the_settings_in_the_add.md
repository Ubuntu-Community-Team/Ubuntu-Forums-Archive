---
title: "kmail doesn't encrypt with the settings in the addressbook"
date: 2011-01-12
forum: Desktop Environments
---

### Post by proxximity on 2011-01-12
I have a problem with kmail: I use it to post on an encrypted mailinglist. So I have defined a contact for the list in the kaddressbook, where in the encryption-settings I selected the keys of all the members of the group - so that when I send mails to the list, it will be encrypted for all of them.
This worked fine for some time now but recently (I can't say exactly after which version - maybe after upgrading to kubuntu 10.10) kmail just doesn't use the encryption-settings from the address-book anymore. So when I select the mail to be encrypted, kmail suggests just the key for the list-address itself - which is of course useless, because I want to encrypt for all the members. So now I have to select the keys manually for every mail i send.

Anyone with the same problem, any help?

---

### Post by malb on 2011-04-08
Hi, 

I can confirm this bug. I opened a bug report on KDE's bugtracker here:

    [https://bugs.kde.org/show_bug.cgi?id=247229](https://bugs.kde.org/show_bug.cgi?id=247229)

and a ticket on Debian's bugtracker here:

    [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=595359](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=595359)

---

### Post by proxximity on 2011-04-08
Hello malb!

I also posted this bug in launchpad some time ago:
[https://bugs.launchpad.net/ubuntu/+source/kdepim/+bug/709830](https://bugs.launchpad.net/ubuntu/+source/kdepim/+bug/709830)

It's funny, just today I considered posting the bug in KDE's bugtrack too. But I first checked the new kubuntu-release (the beta of 11.04) and there the problem does not occur. But of course it's good to have the bug posted anyway.

---

