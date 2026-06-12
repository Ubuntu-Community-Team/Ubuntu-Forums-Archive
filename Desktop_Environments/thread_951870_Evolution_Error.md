---
title: "Evolution Error"
date: 2008-10-18
forum: Desktop Environments
---

### Post by WildeBeest on 2008-10-18
Hardy 64 bit
Evolution 2.22.3.1

I have three mail clients, 2 aol and one gmail.
I get the following error messages when I try to send mail.

**Error while performing operation**.

MAIL FROM command failed: Must issue a STARTTLS command first. n26sm9252ele.18

MAIL FROM command failed: Must issue a STARTTLS command first. 26sm7970071ele.8

MAIL FROM command failed: Must issue a STARTTLS command first. u25sm7956785ele.1

RCPT TO <ws> failed: MISSING DOMAIN IN RCPT COMMAND

Anyone know what the problem is?

I've experienced this also with 7.10

---

### Post by WildeBeest on 2008-10-21
no one?

---

### Post by WildeBeest on 2008-10-24
Hello, hello, is there anybody out there?

---

### Post by WildeBeest on 2008-11-06
No one has experienced this error?

---

### Post by hictio on 2008-11-06
Have you seen [here](https://answers.launchpad.net/ubuntu/+source/evolution/+question/12961)?

---

### Post by WildeBeest on 2008-11-06
yes, I have seen that.

I have 2 aol accounts and a gmail one.

It has worked. I receive mail fine, but sending fails from all 3 accounts.

---

### Post by WildeBeest on 2008-11-24
I give up on Evolution. I'll use thunderbird instead.

---

### Post by tomncc on 2008-11-25
> **WildeBeest said:**
> I give up on Evolution. I'll use thunderbird instead.

I agree !!!!  This Evolution Is as close to Windows XP as anything I have seen in Ubuntu Thunderbird works great in any system. tomncc

---

### Post by mitchroberts on 2008-11-26
Are you using a mail server or anything like that?I use Evolution
and had it setup in just a few minutes with no problems but i didn't put in gmail account just the email i got from my isp.
I have found a lot of email clients have a problem with http email thunderbird was wrote with gmail in mind and does a great job at it...check to see if your account is set for http or pop

---

### Post by tjko on 2008-11-26
> **WildeBeest said:**
> I give up on Evolution. I'll use thunderbird instead.

I had problems just setting up my gmail account on Evolution. Thunderbird works like a charm, however.

Good choice. :)

---

### Post by SpreadFirefox on 2008-11-26
But there is no exchange plugin for Thunderbird :(

---

### Post by Swagman on 2008-11-26
I love Evolution.

But intrepid has buggered the "empty deleted items".

I'm having to go into .Evolution and manually delete.

---

### Post by WildeBeest on 2008-11-26
> **mitchroberts said:**
> Are you using a mail server or anything like that?I use Evolution
and had it setup in just a few minutes with no problems but i didn't put in gmail account just the email i got from my isp.
I have found a lot of email clients have a problem with http email thunderbird was wrote with gmail in mind and does a great job at it...check to see if your account is set for http or pop

No mail server.

Receiving e-mails, aol, gmail works fine in Evolution.
Replying and sending mail fails miserably with the above error messages.

Thunderbird works like a champ.

---

### Post by nooitgedacht on 2010-04-14
In Thunderbird I changed the port for sending mail to 587. It worked well.
Question...Where do you chose port settings in Evolution?

---

### Post by dearingj on 2010-04-14
> **nooitgedacht said:**
> In Thunderbird I changed the port for sending mail to 587. It worked well.
Question...Where do you chose port settings in Evolution?

The same place you put in the name of the server to connect to. After the server's name you add a colon and then the port number. For example, "mail.google.com" would become "mail.google.com:587"

---

### Post by nooitgedacht on 2010-04-14
Works like a charm....:smile:

It is just the port. Set your SMTP server address to:

smtp.gmail.com:587

Error will go and all will be fine. This is not unique to Gmail - I have hosting with eApps who also have SMTP on 587 so require the same treatment.

I personally have nothing good to say about Thunderbird. I found the IMAP support extremely slow, the add-ons buggy and the application generally not fit for commercial use, which is why I switched BACK to Evolution, which has never given me any problems. Just for the record.

---

