---
title: "Best solution for Gmail backup?"
date: 2011-07-25
forum: Desktop Environments
---

### Post by robgr85 on 2011-07-25
Hi there!

Recently, there were some rumours, that google changed their policy and closed some gmail / google+ accounts. That is why I would like to archive all of my online mail on my external harddrive. I've always used online storage without local mail clients and I don't have any experience in that area, so I ask You for help. What linux tool would be the best for this purpose? 

I am looking for some app, that will be as elastic as possible:
- it should let me choose storage folder 
- archived mail format should be easy to import for other mail clients (ability to use into other mail software in the future)

it would be great if:
- mail client would have efficient search feature (one of the major reasons why I use gmail rather than other mail box providers)
- I could sync back downloaded mail (let's say that google shut my account, I would create another and upload my mail there)

Any suggestions?

---

### Post by fdrake on 2011-07-25
easiest way is to open another gmail account just as a backup account and forward all your received and sent messages to the backup address. google has a 'forward to' option.
1. free, no need to be online and it sync instantely.
2.google cannot ban this account because is not sending any messgs at all but is just receiveng email from your account and the ppl that emails you
3. easy to set up and stable, not need to worry for crashes

---

### Post by IWantFroyo on 2011-07-25
You could also use something like Evolution, and set it up as POP. It should pull all of your mail down, and you can back it up (I read about a 'Backup and Restore' plugin).

---

### Post by fdrake on 2011-07-25
do you have to give them your password? hmm...

---

### Post by robgr85 on 2011-07-25
> 
easiest way is to open another gmail account just as a backup account and forward all your received and sent messages to the backup address. google has a 'forward to' option.
1. free, no need to be online and it sync instantely.
2.google cannot ban this account because is not sending any messgs at all but is just receiveng email from your account and the ppl that emails you
3. easy to set up and stable, not need to worry for crashes


Thanks, but I would like to create offline archive once a month (connected with removal from gmail servers). 

> 
Forget all those things.

Simply pay up $7 at [http://www.thegmailbackup.com](http://www.thegmailbackup.com)
and your all gmail messages past 7 years will get backed up neatly automatically.
You can then download it as zip file.

Regards


Thanks, for tip, but I do not want to put my mail passwords to anyone and spread my mail to other servers. I want it offline, safe & secure.

> **IWantFroyo said:**
> You could also use something like Evolution, and set it up as POP. It should pull all of your mail down, and you can back it up (I read about a 'Backup and Restore' plugin).

Yes, I am thinking of getting it on my harddrive through POP. But what client would be the best and most versatile? 
It would be nice to get features like those from thegmailbackup.com (saving [or converting afterwards] mail in nice organized html format, conversations etc). There are lots of POP clients, but what will be the best one for archiving mail? I've heard of evolution, kmail, pine, claws mail but probably there are a lot of others that I do not know about... and could be better for that purpose.

---

### Post by perspectoff on 2011-07-25
Thunderbird allows IMAP, and Google has IMAP.

Thunderbird allows offline storage (and it is the default starting in Thunderbird 3.0, I believe).

You can therefore store all your email offline painlessly.

I did this for both my Google and Yahoo accounts, since they both did something similar.

They're trying to stamp out spam, but they end up stamping out legitimate users.

Further, the US Patriot Act now says that anything you leave on a public server in the US (Yahoo and Google servers count) for 6 months or more can be examined by the US govt without a warrant. (If you want privacy, never leave anything on a public server for more than 6 mos in the US. You should probably never put anything that is unencrypted on any server other than your own anyway).

So, why not set up your own email server?

If is trivial to do. Buy your own domain name (about $3-9 per year from a cheap Domain Name Registrar) and then use dovecot-postfix to install and configure an email server nearly automatically.

Took me about a day.

Now I keep all my email on my own server, instead of on Google or Yahoo.

---

### Post by robgr85 on 2011-07-25
> **perspectoff said:**
> Thunderbird allows IMAP, and Google has IMAP.

Thunderbird allows offline storage (and it is the default starting in Thunderbird 3.0, I believe).

You can therefore store all your email offline painlessly.

I did this for both my Google and Yahoo accounts, since they both did something similar.

They're trying to stamp out spam, but they end up stamping out legitimate users.

Further, the US Patriot Act now says that anything you leave on a public server in the US (Yahoo and Google servers count) for 6 months or more can be examined by the US govt without a warrant. (If you want privacy, never leave anything on a public server for more than 6 mos in the US. You should probably never put anything that is unencrypted on any server other than your own anyway).

So, why not set up your own email server?

If is trivial to do. Buy your own domain name (about $3-9 per year from a cheap Domain Name Registrar) and then use dovecot-postfix to install and configure an email server nearly automatically.

Took me about a day.

Now I keep all my email on my own server, instead of on Google or Yahoo.


Thanks for the solution. I have hosting & domain, but I keep with google because of their fancy built in search engine. I'm not sure if my mail will be safer on my hosting provider, than on such a big company like google. That's why I'm thinking of archiving it at home rather than storing on my webhosting's mail. I want to archive it on on my linux box with mini-ITX motherboard, and after that, remove from gmail account. It would be better to use something without the need of kde/gnome  (security reasons and computing power of my server box), but I can turn X11 on once a month.

I will not redirect all of my mail without usage of google to my home server (at dns level) - in case of downtime at my homeserver I'll lost incoming mail.

Nice to know about that 6 month period. I will speed up the process. Just wonder, how long google stores the backups of our mail messages (I don't think that they delete them after downloading - they probably hide it from us, but messages still exists in databases).

---

### Post by robgr85 on 2011-08-02
a little bump in the thread. 

I've read a lot, and finally decided, that I will try to download all the mail from my multiple gmail accounts to my home-atom-server drive by fetchmail connected with dovecot and roundcube interface (I do not have GUI on my atom-server). 

Just wonder how to correctly setup fetchmail, that it will receive mail from multiple accounts without mixing them into one maildir. Maybe there is something better than fetchmail for that purpose? Any suggestions/tips?

---

### Post by mister_p_1998 on 2011-08-02
Why is google closing Gmail accounts?

Steve

---

### Post by Megaptera on 2011-08-02
I think it's only Google labs, not mail [http://imblogginghere.com/techblog/201107/internet/google-internet/google-labs-closing-not-gmail-or-maps-labs/](http://imblogginghere.com/techblog/201107/internet/google-internet/google-labs-closing-not-gmail-or-maps-labs/)

... but send three and four pence we're going to a dance!

---

### Post by Alexandre Putt on 2011-08-02
First of all, you can use an email client (like Evolution) to download all email for offline viewing (through IMAP, no need to bother with outdated and limited POP). 

However, I'd recommend spending a day to learn how to configure **fetchmail** for use with e.g. **mutt**. This allows to automatically download all email and store it in a text format where and how you like it (not necessarily for use with mutt, but anything).

---

### Post by robgr85 on 2011-08-03
All of my mail is now stored on my private atom-server, accesible by imap from other machines. Solution very similar to one explained below:

[https://help.ubuntu.com/community/POP3Aggregator](https://help.ubuntu.com/community/POP3Aggregator)

And there is brand new, stupid question ;-) about gmail forwarding/redirecting. Supposing I want to receive emails larger than gmail's size limit - is there a way to redirect mails to my private server [I know that I would need to install another app], so that it isn't blocked on gmail server because of its size? I've looked at gmail settings tabs, but there seems to be only forwarding (will it work for that purpose?) ...and changing google DNS MX records for my mail alias is probably impossible...

---

### Post by wildmanne39 on 2013-03-16
old thread closed!

---

