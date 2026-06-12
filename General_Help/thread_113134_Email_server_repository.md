---
title: "Email server repository?"
date: 2006-01-05
forum: General Help
---

### Post by Goonbridge on 2006-01-05
Hi

I'm new to these forums, despite lurking for what seems like forever and taking advantage of many a solution posted here. So first of all thank you, Ubuntu on its own wouldn't be worth anything to me if it wasn't for these forums.

I have setup a basic 'server'. It handles my SMB shares, crunches away on F@H and doe's a whole heap of other cool stuff. 

Ideally what I want it to do is act like an exchange server of sorts. That is download my pop mail into a repository, and allow me to access said mail from an Outlook 2003 client. I would like to send mail via the server as well, and if possible have my mail so it's easy to backup and manage.

From what I understand, fetchmail is half the solution - but I'm unsure of how I can get Outlook to tap into the emails. I have about 3 accounts that would need to be accessed, although I only need to send via 1 SMTP account. I would like to handle SMTP on the Ubuntu box, so virus scanning and everything is managed from there.

Can anyone point me in a direction of a fairly easy to understand guide for how I can achieve this?

Thanks for your time :smile:

---

### Post by amohanty on 2006-01-05
Take a look at this tutorial:
[http://www.hypexr.org/linux_mail_server.php](http://www.hypexr.org/linux_mail_server.php)

You can install most of the stuff using synaptic or apt-get.
If you have any questions post back here.

HTH
AM

---

### Post by Goonbridge on 2006-01-05
Thanks for the quick reply.

I am wanting to keep my configuration fairly simple at the moment, so I will probably do away with spam assasin and squirrelmail.

After looking at that guide I will attempt to setup fetchmail to hold the mail in a folder, then setup courier-imap to serve the emails to my windows pc.

Is there anything else I will need initially? (I realise I have left out SMTP configuration, but will look into that later on.)

---

### Post by amohanty on 2006-01-05
I think you will still need an MTA like Postfix, Qmail, or Courier's server. AFAIK Courier IMAP works in conjunction with an MTA that uses maildirs. I havent done this in a while so I cant say for sure, but please verify this before you skip on an MTA.

HTH
AM

---

