---
title: "Using Evolution to connect to a GMail IMAP server"
date: 2009-02-03
forum: Desktop Environments
---

### Post by petersfreeman on 2009-02-03
I'm trying to set up Evolution to connect to my IMAP service on GMail.  I need to use IMAP as I access my mail on different computers in different towns and I want the mail to stay on the GMail server.

I can receive my mail headers fine and I can read my mail, however when I go to send mail, it does not work as I don't seem to be able to set the ports as GMail needs.  GMail settings for "other" mail clients are at:

[http://mail.google.com/support/bin/answer.py?answer=78799](http://mail.google.com/support/bin/answer.py?answer=78799)

The instructions read:

---------------------------------------------

Incoming Mail (IMAP) Server - requires SSL:  	imap.gmail.com
Use SSL: Yes
Port: 993

Outgoing Mail (SMTP) Server - requires TLS: 	smtp.gmail.com (use authentication)
Use Authentication: Yes
Use STARTTLS: Yes (some clients call this SSL)
Port: 465 or 587

Account Name: 	your full email address (including @gmail.com) Google Apps users, please enter [email]username@your_domain.com[/email]

Email Address: 	your full Gmail email address (username@gmail.com) Google Apps users, please enter [email]username@your_domain.com[/email]

Password: 	your Gmail password

Please note that if your client does not support SMTP authentication, you won't be able to send mail through your client using your Gmail address.

Also, if you're having trouble sending mail but you've confirmed that encyrption is active for SMTP in your mail client, try to configure your SMTP server on a different port: 465 or 587. 

-------------------------------------------------

Does anyone know a solution to this problem?

Thanks,

Peter

---

### Post by petersfreeman on 2009-02-03
I found solution, I had it the Sending Mail set to TLS and when I set it to SSL everything worked fine.

Peter

---

### Post by Grumpey on 2009-02-03
Out of curiosity how did you set up the sent folder in evolution?

---

### Post by petersfreeman on 2009-02-19
Hi Grumpy,

I set up the Sent folder to be Google Mail/Sent as I want my sent mail to stay on the IMAP server.

Cheers,

Peter

---

### Post by adahhh on 2009-03-04
> **petersfreeman said:**
> I found solution, I had it the Sending Mail set to TLS and when I set it to SSL everything worked fine.

Peter
Hi,
I tried this solution but it didn't work for mi. I need send my mail urgently because it's my professional mail... 
Any help, please.?

Thank you,

---

### Post by petersfreeman on 2009-03-30
Hi Adahhh,

The two settings I changed are:

Edit/Preferences/Mail Accounts/Edit/Defaults/Sent Messages Folder: [Choose the Sent Folder on your IMAP Google Mail Account]

Edit/Preferences/Mail Accounts/Edit/Sending Email/Security/Use Secure Connection: SSL Encryption

Cheers,

Peter

---

### Post by jamesobooth on 2009-04-04
Also, you can specify the port by entering the server name followed by a ":" then the port number (no spaces)

Mine looks like this for gmail and works perfectly:

smtp.gmail.com:587

---

