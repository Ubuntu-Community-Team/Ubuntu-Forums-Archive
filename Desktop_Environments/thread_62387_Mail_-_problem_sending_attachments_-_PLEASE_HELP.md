---
title: "Mail - problem sending attachments - PLEASE HELP"
date: 2005-09-04
forum: Desktop Environments
---

### Post by alquimista on 2005-09-04
Hi,

I'm sorry to post it again; there was no answers for my previous post. The problem is that in Kontact, when sending mails with attachments I get the error (translated from spanish): "could write on smtp.gnsis.net file"; normal mails (with no attachment) can be sent with no problems at all. 
In other news groups they suggested it could be the timeout parameter for the SMTP server, so in KControl I modified the "Server Response Time" to 2,600 senconds, but the problem remains.
Using CorssOver, I tryed MS Outlook, and the message was: 451 Timeout  (#4.4.2). 
Using Evolution, I get: "DATA command failed: broken pipe: mail not sent".
On WinXP using Outlook, I don't have this problem.

What could it be? 

Thank you,
Guillermo

---

### Post by alquimista on 2005-09-04
Sorry; I did not write the Kontact error message correctry; I get "could NOT write on smtp.gnsis.net file"

---

### Post by drx on 2005-09-04
Hi, have you tried to set up an external mail server? Like the one you are using with Windows?

---

### Post by alquimista on 2005-09-04
How can I setup an external mail server? I was not aware I had that in Windows; there I just configured Outlook with my POP and SMTP servers as I did in Kontact.
In the #Kubuntu-es a friend suggetsed me to use sendmail instead of SMTP... apparently the attachment was sent, but checking the mailQ, I found that the mail was still there and never sent.

Thanx,
Guillermo

---

