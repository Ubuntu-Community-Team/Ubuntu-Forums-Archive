---
title: "Fetchmail"
date: 2009-02-05
forum: General Help
---

### Post by sim085 on 2009-02-05
I do not know if this is the best place to ask this, however I really do not know where else to ask!!

I have installed fetchmail on Ubuntu 8.10 Server Edition and configured it correctly. However I either configured it incorrectly or else selected the wrong tool for the job!

Basically I have created a Mail Server and I can successfully send email from my account (me@mydomain.com) to hotmail account (me@hotmail.com) and so on. However I could not send emails from the hotmail account to my account.

I did a little research on the Internet and found out about fetchmail. After a little bit more research I found out how to configure it. 

On my ISP I created an account which catches all emails (all@mydomain.com). This account catches any email sent to @mydomain.com including [email]me@mydomain.com[/email].

Now fetchmail setting smtpname confused me. I set this equal to [email]postmaster@mydomain.com[/email]. The problem is that any email I send to [email]my@mydomain.com[/email] from [email]me@hotmail.com[/email] is sent to [email]postmaster@mydomain.com[/email] and not to the correct receiver.

I checked the mail logs and found out that fetchmail is changing this. I tried to omit this setting but then fetchmail tries to send the email to [email]all@mydomain.com[/email]!!

I do not know what else to try. I have no experience with fetchmail and therefore do not know if it can be used to retrieve emails from ISP server and post them to the address for which they where originally sent!

Anyone knows anything about the subject?

---

