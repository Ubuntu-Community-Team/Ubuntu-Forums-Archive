---
title: "Edit Postfix's from line"
date: 2010-10-23
forum: Desktop Environments
---

### Post by brcre on 2010-10-23
Here is the problem.
If I send mail from the command line the recipient gets an email from: myusername@mycomputername (i.e. brcre@chimera) and this always gets flagged as junk mail by mail servers.

What I would like to do is change that line to my real email address and hopefully stop it from getting flagged.

Any ideas?  I obviously don't know the right question to ask because my search results are not coming up with anything useful or even remotely close to what I'm trying to do.

---

### Post by acreech on 2010-10-23
I have never messed with Postfix before. but look at this webpage and see if that is any help. 


[HTML]http://www.davidgrant.ca/setting_up_postfix_to_send_outgoing_mail_on_ubuntu[/HTML]

```
Update (2007-07-19): When I changed ISPs, my new ISP did not like my 
From: address being david@centurion (I just named it after the case model). 
So I had to do the following. Add this to /etc/postfix/main.cf:

smtp_generic_maps = hash:/etc/postfix/generic

Add this to /etc/postfix/generic:

@centurion      david@telus.net

I just made up an email address there to make it happy.
Don't forget to run sudo postmap /etc/postfix/generic
```

---

### Post by acreech on 2010-10-23
This page deals direclty with "Relaying Postfix SMTP via smtp.gmail.com" see if this helps you. 

```
http://ubuntu-tutorials.com/2008/11/11/relaying-postfix-smtp-via-smtpgmailcom/
```

---

