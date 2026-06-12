---
title: "PHP+Mail"
date: 2008-12-17
forum: General Help
---

### Post by clR3VV on 2008-12-17
Hey guys, I have a php script now that needs to send an email. This is when i relized that i need to setup a mail server or something on my ubuntu server. Yet i'm pretty new to ubuntu, so I really have no idea what i need to do.

---

### Post by doobiest on 2008-12-17
Install sendmail

You don't really need an email server you just use php and sendmail to connect to an SMTP server just like a regular email client would

[http://ca3.php.net/mail](http://ca3.php.net/mail)

---

### Post by albhardyf on 2008-12-17
What mail server do you want to implement you could go for postfix or sendmail both should be easy enopugh to install but it gets hard when you start to configure and lock down etc.
To install either open a terminal that is under Application ->Accessories ->Terminal then type the following commands at 
your prompt which  should say something like <yourusername>@<servername>:~$
type [su -]
the system will ask for your root password - enter your root password
your prompt should now say something like root@<servername>:~#
you can then 
type [apt-get update && apt-get install postfix]
OR instead of apt-get install postfix you can 
type [apt-get install sendmail] 
to install either or you could have just typed at your user prompt <yourusername>@<servername>:~$
type [sudo apt-get install postfix]
 the system requests your password which you enter OR
type [sudo apt-get install sendmail] 
the system requests your password which you enter
For the configs just google sendmail.conf or howto configure postfix. it's not easy but it's more than worth it.

---

### Post by doobiest on 2008-12-17
If you're only looking to send outgoing emails from a php script. Let say a webpage that sends out notifications of some sort, stick with sendmail. Once you have it installed and using the mail() function of php there should be 0 configuration required out of the box.

All the mail function is doing is taking the subject/body and recipient address and passing it to sendmail. Then sendmail will take the domain from the recipient address and do an MX lookup on that domain. From there it gets the MTA/SMTP server for that domain and hands off the email.

That is how my server is configured.   If you're also looking for inbox mail I would set up postfix as it's way cooler and then install something like dovecot IMAP server.

---

### Post by clR3VV on 2008-12-17
Thanks for the fast reply, i just did apt-get install sendmail, and it works now!

---

