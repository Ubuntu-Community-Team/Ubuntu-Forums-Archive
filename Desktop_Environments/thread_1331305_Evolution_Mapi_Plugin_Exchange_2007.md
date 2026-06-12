---
title: "Evolution Mapi Plugin Exchange 2007"
date: 2009-11-19
forum: Desktop Environments
---

### Post by svenole on 2009-11-19
Hello. 

For two years now, I've been waiting for Evolution to support Exchange 2007 environments. I'm running Ubuntu 9.10 Karmic and found that the mapi plugin was available. I found out kind of early that the version included was so buggy that I could not use it, so I deinstalled it and used a newer version not yet available via update (evolution-mapi-0.28.1). 

With this plugin, evolution actually starts and connects to Exchange 2007 server. There are still a whole lot of problems, but I got up my Inbox, got the calender synced and could after some struggeling use the GAL. 

However I have two major problems.

1. I can not send emails. Emails to collegues on the same exhcange server, fails completely with error message (could not send email). Email to external users gives the same error message and stays in the Outbox, but the mail is actually processed and delivered to the external recipient. Now and then I get an error message back from the Exchange server telling that the recipient couldn't be found (domain user with a lot of tags)

2. The text coding is not working. I've confgured it to ISO-8859-1. However I need to use the View-menu in each email to set this pameter every time I want to read an email from collegues on the same Exchange server. This seems to work fine on emails from externals. 

I should probably stay with my VMware Player / Win 7 set up for reading email and wait for new versions of the mapi plugin to be developed, but I decided to give the forum a chance.. Anyone out there that can bring some new ideas in to this? 

- sven

---

### Post by PhoneixS on 2009-11-20
If you see in [http://www.go-evolution.org/MAPIProvider](http://www.go-evolution.org/MAPIProvider) it say > Sending Mails. (Plain text + Attachment). Are you trying to send html mails or confirmations?

And I have the same coding problem.

I have the 9.10 versión of ubuntu, evolution 2.28.1 and evolution-mapi 0.28.1.

---

### Post by svenole on 2009-11-21
Well. 

The docs you refer to is a year old... However I can see that there is a connection with samba4 which is something that I have not seen before. The combination I run today is: 

Ubuntu 9.10 
evolution 2.28.1
evolution mapi 0.28.1 (manually compiled and installed)
default samba (samba-common 2:3.4.0-3ubuntu5.1, samba-common-bin-2:3.4.0-3ubuntu5.1)

I´m also using the default samba version included in Ubuntu. I can see that samba4 is there, but it is not installed. Is this a prerequisite for evolution-mapi to work? If so, I need to be careful. I´m using samba all the time to do my work and if samba4 screws this up, I have an even bigger problem.....

---

### Post by r0cketman on 2010-03-16
It looks like this has been [bugified]("https://bugs.launchpad.net/evolution-mapi/+bug/361993?comments=all").  Please feel free to hop on to the bug and provide any feedback or debug information.  The more people we get squawking about this, the higher priority it will get.

---

### Post by wolfteeth on 2010-07-29
yes, I also have same issues that cannot to sent out and besides, the email reading speed is quite slow...since my e2k7 server is not located at my office side but wide, so without cache mode, the speed would not be accepted. I have to give up.


> **svenole said:**
> Hello. 

For two years now, I've been waiting for Evolution to support Exchange 2007 environments. I'm running Ubuntu 9.10 Karmic and found that the mapi plugin was available. I found out kind of early that the version included was so buggy that I could not use it, so I deinstalled it and used a newer version not yet available via update (evolution-mapi-0.28.1). 

With this plugin, evolution actually starts and connects to Exchange 2007 server. There are still a whole lot of problems, but I got up my Inbox, got the calender synced and could after some struggeling use the GAL. 

However I have two major problems.

1. I can not send emails. Emails to collegues on the same exhcange server, fails completely with error message (could not send email). Email to external users gives the same error message and stays in the Outbox, but the mail is actually processed and delivered to the external recipient. Now and then I get an error message back from the Exchange server telling that the recipient couldn't be found (domain user with a lot of tags)

2. The text coding is not working. I've confgured it to ISO-8859-1. However I need to use the View-menu in each email to set this pameter every time I want to read an email from collegues on the same Exchange server. This seems to work fine on emails from externals. 

I should probably stay with my VMware Player / Win 7 set up for reading email and wait for new versions of the mapi plugin to be developed, but I decided to give the forum a chance.. Anyone out there that can bring some new ideas in to this? 

- sven

---

