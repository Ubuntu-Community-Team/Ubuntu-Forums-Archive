---
title: "How to send e-mail from within an application in Gutsy"
date: 2009-04-22
forum: General Help
---

### Post by zelalem on 2009-04-22
Hi all, I am using ubuntu Gutsy. I am developing an application for voip mail and I want to send e-mail to my mailserver (which is on the same domain) from the voip mail application. So, I want to send an e-mail from my application like I do from an e-mail client. I have been googling around since yesterday but i couldn't get anything. configuring sendmail seems frustrating. Please anyone can help me. Basically I want my application to send e-mail to different users using my e-mail account through the mail server in my domain (which is configured to send and recieve e-mails). I don't want to recieve e-mails. I only want to send out. 

Thanks.

---

### Post by shel-hall on 2009-04-22
> **zelalem said:**
> Hi all, I am using ubuntu Gutsy. I am developing an application for voip mail and I want to send e-mail to my mailserver (which is on the same domain) from the voip mail application. So, I want to send an e-mail from my application like I do from an e-mail client. I have been googling around since yesterday but i couldn't get anything. configuring sendmail seems frustrating. Please anyone can help me. Basically I want my application to send e-mail to different users using my e-mail account through the mail server in my domain (which is configured to send and recieve e-mails). I don't want to recieve e-mails. I only want to send out.
"ssmtp" works nicely for this, and the config is dead simple.  Actually using it to send mail would depend on the type of language you're using for development, of course, but, in general, you can just pipe some text into the "mail" program, specifying the subject and addressee on the command line.

-Shel

---

### Post by Cheesemill on 2009-04-22
Check out the post I made in this thread (it's the second post):

[http://ubuntuforums.org/showthread.php?t=1119257]("http://ubuntuforums.org/showthread.php?t=1119257")

If you follow my instructions you can set up email relaying through your current server in a couple of minutes.

Cheesemill

---

### Post by zelalem on 2009-04-22
Hi cheesemill, thank you for your info. I followed the link and tried to send an e-mail but nothing happned. There was also no error. BTW, how does the mailserver authenticate me. I mean I didn't supply my user name and password for the mailserver (to the one exim will relay the e-mail to) when i reconfigure exim4-config?. BTW, when it finishes reconfiguring exim, I got the following message:

* Stopping MTA for restart                                           [ OK ]
 * Restarting MTA                                                       [ OK ]
** * ALERT: **exim paniclog /var/log/exim4/paniclog has non-zero size, mail system possibly broken             (what do you think is this alert talking about?)

Please advice me how I can do that.

---

### Post by zelalem on 2009-04-22
> **shel-hall said:**
> "ssmtp" works nicely for this, and the config is dead simple.  Actually using it to send mail would depend on the type of language you're using for development, of course, but, in general, you can just pipe some text into the "mail" program, specifying the subject and addressee on the command line.

-Shel
Hi Shel-Hall, thank you for your response. I also tried ssmtp yesterday, but the mail command always referes to sendmail not ssmtp. So, I wasn't successful in that regard. Can you tell me how I can do it? I mean how I can make the ssmtp to be default smtp engine?

Thank you.

---

