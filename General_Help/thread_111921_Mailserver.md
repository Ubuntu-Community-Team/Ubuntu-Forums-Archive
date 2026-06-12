---
title: "Mailserver"
date: 2006-01-03
forum: General Help
---

### Post by tbresson on 2006-01-03
Hi there.

I'm running Ubuntu 5.04 and like to run a mail server. Nothing major or anything, just for the fun of it really. Mostly it will be used as a testing scenario for my web development.

I tried to look around for some help but most of the things I found was pretty complicated. I have a very simple setup: 1 domain and only a few users. I only need to run a regular smtp/pop3 server, no IMAP, webmail, spam filter, anti-virus, proxy, encryption or anything like that.

Could anyone be helpful setting me up?

I have noticed some mailserver components like PostFix and Courier - are they any good, easy to setup or? I was also recommended Xmail but I'm having trouble already. I tried downloading phpxmail but I can't get it to work - it needs a CTRL account or something and I'm blank of ideas, of course I tried [email]root@mydomain.xxx[/email] and the root password but no luck.

---

### Post by tbresson on 2006-01-05
Hmm.. no much help in here.

Well.. I was determined so I think I might have solved it myself. At least the hard part I guess.

So if anyone else has issues with mailservers here's the way I got it to work.

I downloaded the PHPXMAIL and placed it in /var/www/phpxmail
I opened the afterly created servers.php and copied the encrypted password (the username can be anything you like, they suggest you don't use an existing user on your system and not an e-mail, e.g. mailadmin).

Open the /etc/xmail/ctrlaccounts.tab and set in:
"<username>"<tab>"<encrypted_password>"
/newline

The " are needed around the username and password and <tab> means, press tab between the values.

/newline is just to indicate you need a newline after the user info.

That's it. You can now logon to PHPXMAIL and configure your XMAIL server.

NB!! Remember to read the readme of the xmail server it strongly suggests to setup 2 minor changes in the default config to prevent others using your mailserver as relay server (a relay server is a spammers wet dream).

---

