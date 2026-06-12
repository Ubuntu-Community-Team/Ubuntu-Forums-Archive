---
title: "Acquire kerberos ticket"
date: 2006-02-20
forum: Desktop Environments
---

### Post by zajmon on 2006-02-20
Hi!
I have followed this guide ([https://wiki.ubuntu.com/ActiveDirectoryWinbindHowto]("https://wiki.ubuntu.com/ActiveDirectoryWinbindHowto")) to use Active Directory as domain controller for my linux client. This works without any problems, but I really need to acquire a kerberos ticket when a user login to the client without any need to run kinit after login. This is because there will be homefolders on the AD-computer so I need the kerberos ticket to veryfy the user to its homefolder.

I am very greatfull for any help I can get, and remember, I am not a linux expert ;)

Sorry for my bad english...
//Simon

---

### Post by nocturn on 2006-02-20
If you authenticated with your kerberos password, you should already have a ticket.

What does klist say?

---

### Post by zajmon on 2006-02-21
Yes, I think so too, but if I run klist no tickets are cached. The guide allso says that no ticket will be cached, but he does not write any sollution to acqire a ticket at logon. I have no idea how to solve this, but there must be a way! It is really wierd no ticket is cashed :S Thanks for any help.

---

### Post by nocturn on 2006-02-22
[QUOTE=zajmon]Yes, I think so too, but if I run klist no tickets are cached. The guide allso says that no ticket will be cached, but he does not write any sollution to acqire a ticket at logon. I have no idea how to solve this, but there must be a way! It is really wierd no ticket is cashed :S Thanks for any help.[/QUOTE]

Are you using pam_winbind or pam_krb5 in /etc/pam.d/common-auth?

I have pam_krb5 against a Linux Kerberos server, and it does cache a ticket.

---

### Post by zajmon on 2006-02-22
Hmm, I don't know right now, but I will check next week, I have the instalation in our network lab in school. I think my friend have come up with a sollution using pam_mount, I will check it out next week and reply then.

---

