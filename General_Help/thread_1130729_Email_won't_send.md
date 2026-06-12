---
title: "Email won't send"
date: 2009-04-20
forum: General Help
---

### Post by mark.giblin on 2009-04-20
All the threads I have trawled all go on about setting up the email clients.

I have no problem in that score, however... emails incoming are fine and outgoing are not.

I installed the MTA scripts through the package installer.

After reboot, no change.

Question 1. Why does linux ship desktops without this function installed ready to use or even enabled?

Question 2. What now?

---

### Post by Thyme on 2009-04-20
Hi Mark,

What email client are you using and what MTA are you using? I was able to send/receive after a default Edgy install, w/ sendmail and evolution.

---

### Post by mark.giblin on 2009-04-20
I am using Opera, the same situation applies to the default evolution mail client, it too has problems with outgoing mail, incomming is not an issue.

Some system log said something about sendmail is not installed.

So I looked on Ubuntu help and all I found for sendmail was loads of infomation on how to configure email clients to send and receive emails but non to help with the issue of sendmail not working or installed. I found a page about installing the MTA package to solve the issue by using the package installer in ubuntu to install the previously mentioned package... Still nothing.

The settings in the email client are no different than the ones on my laptop running WinXP, again I am using Opera on that machine and that has no issues with sending mail.
> Apr 20 10:40:01 markgiblin-desktop /USR/SBIN/CRON[6299]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Apr 20 10:40:06 markgiblin-desktop sm-msp-queue[6328]: My unqualified host name (markgiblin-desktop) unknown; sleeping for retry
Is what I find in the syslog. 

If the MTA package's job is to send mail out, why isn't it doing so?

---

### Post by mark.giblin on 2009-04-25
Still cant get incoming emails.

Anyone got an idea what the issue is or what I need installed? 

To Re-cap: -

pop & smtp have same URL

I can get pop

I can't smtp

Tried this with firewall configured

Tried this with firewall off

Still no change...

I installed MTA as per one article I did find but that made no difference.

So either the sendmail or MTA need some configuration and I havent a clue on what to do to get email outgoing to my web mail servers provided by the hosting company for my web domain.

All the articles I do find all seem to be centered around setting up servers for this, not what I want, all I need is to beable to connect to my web host servers, while it is happening for pop, nothing for smtp.

---

### Post by wilcan34 on 2009-04-25
PRETTY MUCH THE SAME FOR ME TO
 ANY hELP?
W

---

### Post by darkstaar on 2009-04-26
> **mark.giblin said:**
> ... emails incoming are fine and outgoing are not.. What now?

You haven't indicated whether or not you get any error messages.

ISP's are increasingly blocking port 25 for outgoing mails on SMTP for mail accounts not from their own domain. Could this be your problem?

For example, if you're trying to send out an e-mail from the account 'john@yourdomain.com' then your ISP may be blocking this on port 25, the traditional SMTP port. However, there's usually an easy way around this. Simply change the outgoing port. Port 587 should work.

In Evolution, just change the server configuration for each account to something like smtp.yourdomain.com:587 . In Thunderbird, just change all of your SMTP Server settings to use port 587.

Not sure if this might me your problem but it's a common one.

--Leisa

---

### Post by sir_nasty on 2009-04-26
any chance you're using a sonic wall router....?  If so bypass it and try again, they like to block port 25...  Also, double check to see if your 'working' mail machine has outgoing server authentication enabled....

---

### Post by wilcan34 on 2009-04-26
Server is paradise.net.nz
Can send to paradise accs. and receive.
when sending to other accs. .com,.co,etc get error mess. "relaying not permitted"
Instaled postfix,restarted,
still no success!
Thanks for suggestions
W

---

### Post by mark.giblin on 2009-04-26
> **darkstaar said:**
> You haven't indicated whether or not you get any error messages.

ISP's are increasingly blocking port 25 for outgoing mails on SMTP for mail accounts not from their own domain. Could this be your problem?

For example, if you're trying to send out an e-mail from the account 'john@yourdomain.com' then your ISP may be blocking this on port 25, the traditional SMTP port. However, there's usually an easy way around this. Simply change the outgoing port. Port 587 should work.

In Evolution, just change the server configuration for each account to something like smtp.yourdomain.com:587 . In Thunderbird, just change all of your SMTP Server settings to use port 587.

Not sure if this might me your problem but it's a common one.

--Leisa

HSDPA Modem <--- With these, you do not get anything other than direct connection to the internet, ISP services like webserver space or mail are not included, all you get is internet access.

I have no issues with same set up under WinXP, so the issue is not my Internet provision, its is Linux that is the issue and the host company I use provide domain specific mail servers...

I have no access to the mail server, for security reasons, the hosting company provide the tools to make, delete and change user passwords in a control pannel that is also used to set up services like forum boards, CMS, etc. Email settings in Opera are the same as in the WinXP install of Opera.

The issue is in Linux, its either a config thing or its missing something and I have no idea where to look to check the config of sendmail and MTA.

---

### Post by mark.giblin on 2009-05-01
Still got nothing happenig with outgoing emails...

---

### Post by mark.giblin on 2009-05-05
Anyone here able to point me in the right direction please?

All I want is for the MTA or Sendmail or whatever "Missing Component" or cnfiguration information to get the SMTP to connect to the remote web host mail server so I can send mail from my host account.

I am not being blocked or have any obstructions by the ISP I use or any port blocking...

THIS IS A LINUX ISSUE and nothing more.

So some help would be nice as it seems to be a bit thin on the ground.

---

### Post by Rhubarb on 2009-05-11
Have you tried booting off an ubuntu live CD, then using evolution for your email (make sure to tell it to leave messages on server, as you don't want to download any emails when you're just testing it).
Try this without making any changes to your firewall, or other settings, just internet and email configuration.

Personally I've had no problems at all with getting pop3 / imap / smtp email working in all Ubuntu versions from 5.10 to 9.04 so far.

If that doesn't work, consider sending an email to your email provider (yes I know it's a bit of a catch 22 problem with this) asking if there's any known issue with sending emails in linux to their smtp mail server.
There may be information on your email provider's faq / wiki / forum about this too.

I do hope you get your email sorted out soon.

---

### Post by mark.giblin on 2009-05-11
I will give your suggestion a go of trying the live CD.

Will see what happens...

---

### Post by wilcan34 on 2009-06-28
Solved.
Reloaded evolution.reinstalled,and is now working .
Thanks to all for the help
W

---

### Post by gary1965 on 2010-04-04
Hi I know it has been a while but I too am a new user with the same issue.

I can receive email but not send.

I am a virgin media customer

Did you just reinstalll Ubuntu I cannot tell from your post

Thanks

---

