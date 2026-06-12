---
title: "SMTP opinions welcome"
date: 2008-12-10
forum: General Help
---

### Post by prem1er on 2008-12-10
Hey everyone,
  Starting to build a new website and I just realized that I will be needing a mail server for several purposes on my site.  I'm not sure if it matters, but I'm building my site using Django web development framework.  I was just wondering what mail servers people have had success with on Ubuntu server.  Links to documentation/tutorials would be appreciated.  Thanks!

---

### Post by Titan8990 on 2008-12-10
Your two main options are Postfix and Exim4.

Exim4 is the official SMTP server for Debian

Postfix is the official SMTP server for Ubuntu


My experience has been with Exim4 and it has been a good experience. I have heard that Postfix is easier to set up.

---

### Post by prem1er on 2008-12-10
> **Titan8990 said:**
> Your two main options are Postfix and Exim4.

Exim4 is the official SMTP server for Debian

Postfix is the official SMTP server for Ubuntu


My experience has been with Exim4 and it has been a good experience. I have heard that Postfix is easier to set up.

Thank you.  I have tried the tutorial here [https://help.ubuntu.com/community/PostfixBasicSetupHowto]("https://help.ubuntu.com/community/PostfixBasicSetupHowto") 

with little luck.  As soon as I switch to a 'Maildir-style' email nothing seems to want to work anymore.

---

### Post by Titan8990 on 2008-12-10
On my Exim server I had to manually create the mail directory. Can you verify that the mail directory exists in each users home folder?

---

### Post by prem1er on 2008-12-10
> **Titan8990 said:**
> On my Exim server I had to manually create the mail directory. Can you verify that the mail directory exists in each users home folder?

Yes.  It exists.

I just found a new tutorial here that might explain why it isn't working.  Seems like the other one was incomplete.

[https://help.ubuntu.com/community/Postfix]("https://help.ubuntu.com/community/Postfix")

---

### Post by Titan8990 on 2008-12-10
It looks like that guide lacks the installation of a MDA (mail delivery agent) such as an IMAP or POP server. However, I did look through it pretty quickly.

---

### Post by Dr Small on 2008-12-10
> **prem1er said:**
> Yes.  It exists.

I just found a new tutorial here that might explain why it isn't working.  Seems like the other one was incomplete.

[https://help.ubuntu.com/community/Postfix]("https://help.ubuntu.com/community/Postfix")


Yes, that guide right there is the one that I always use for setting up Postfix ;)

---

### Post by prem1er on 2008-12-10
Thanks everyone.  Giving it a shot now.  I'll post any results.

---

### Post by iponeverything on 2008-12-10
Don't forget DJB's qmail. It's lean and secure.

---

### Post by tornadof3 on 2008-12-10
I've always found sendmail to be very good and very simple. To get it to receive email from the external network, change the line in /etc/mail/sendmail.mc

FROM:
DAEMON_OPTIONS(`Family=inet, Name=MTA-v4, Port=Smtp, Addr=127.0.0.1')dnl

TO:
DAEMON_OPTIONS(`Family=inet, Name=MTA-v4, Port=Smtp, Addr=0.0.0.0')dnl

and reboot (or restart the server).

If you also install the "mail" command line tool, you can even get mail sent from the command line.

---

### Post by Titan8990 on 2008-12-10
Sendmail? With its security history and cryptic config files that need macros to write them? Seriously?

---

### Post by tornadof3 on 2008-12-10
I downloaded the sendmail package, edited that 1 single line, and had it working exactly to my requirements inside five minutes. And security problems of old are not that evident in the newer releases.

---

### Post by Titan8990 on 2008-12-11
I'm guessing it isn't configured for open relay be default like most mail servers?

If that is only configuring you did it sounds like your machine is just waiting to me exploited by spam bots.

---

