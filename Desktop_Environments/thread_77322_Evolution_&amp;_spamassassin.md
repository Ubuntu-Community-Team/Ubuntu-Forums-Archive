---
title: "Evolution &amp; spamassassin"
date: 2005-10-16
forum: Desktop Environments
---

### Post by JMW on 2005-10-16
Evolution works great except that there is no spam filtering whatsoever. I have spamassissn installed. I've seen the other posts here about this problem. Perhaps I'm a bit thick, but I have yet to find an answer... Any direction would be greatly appreciated...

---

### Post by scubajeff on 2005-10-24
After upgraded from Horay to Breezy, the Evolution and spamassassin linking seems to be broken. I lost all the spam filtering function. Even when I click on the spam and nospam icon on the menu bar, the status line doesn't show the "Learning..." message as it did before in Horay.

Anybody have the same issue?

---

### Post by djjuice on 2005-10-24
I'm glad to see a thread on this.. I hope to see some answers. I have installed spamassian and even spambayes without any luck

---

### Post by MrMunson on 2005-10-25
Same here... Fresh install....

---

### Post by Darrin on 2005-11-10
Im with you all. I installed Spamassassin and set it to enable 1 and nothing was being filtered. I now just set my mail up to go through [Barracuda Networks]("http://www.barracudanetworks.com"). IT works better than spamassasin anyway.

---

### Post by dcstar on 2005-11-11
[QUOTE=scubajeff]After upgraded from Horay to Breezy, the Evolution and spamassassin linking seems to be broken. I lost all the spam filtering function. Even when I click on the spam and nospam icon on the menu bar, the status line doesn't show the "Learning..." message as it did before in Horay.

Anybody have the same issue?[/QUOTE]
My Evolution and Spamassassin worked fine after the Breezy upgrade - does your /etc/default/spamassassin file contain:

ENABLED=1

to turn on spamd?

Do you also have the "spamc" package installed (I believe it is required for mail checking)

My /var/log/mail.log file is filled with spamd messages outlining the work it is doing for my Evolution mail.

---

### Post by scubajeff on 2005-11-12
Yes, the spamassassin is enabled in it's configuration file and i have spamc installed. It worked in Horay, but lost the linkage after upgrade to Breezy.

But anyway, I follow this thread just know if someone will give a hint to this problem. I have already switch to Sylpheed-Claws and Bogofilter combination. More flexible.

---

### Post by btdown on 2005-11-14
I have the same symptoms as scubajeff, but my install was a clean install (not an upgrade from Hoary). Is anyone able to solve this?
BT

edited to change name..

---

### Post by dcstar on 2005-11-15
[QUOTE=btdown]I have the same symptoms as dcstar, but my install was a clean install (not an upgrade from Hoary). Is anyone able to solve this?
BT[/QUOTE]
My "symptom" is that it works fine for me.

---

### Post by fct on 2005-11-30
I *believe* the problem is that evolution-plugins includes the mandatory spamassassin plugin, but doesn't say so in the package description.

Make sure you have installed evolution-plugins and check if it works after installing it.

---

### Post by thegnark on 2005-11-30
[quote=scubajeff]After upgraded from Horay to Breezy, the Evolution ... seems to be broken[/quote] 

yes... yes indeed

---

### Post by btdown on 2005-11-30
Im working from a stock install from Breezy, and it isn't working either. I do have the evolution-plugins installed with the junkmail plugin active. I hope this is fixed in Dapper. ;)

---

### Post by Darrin on 2005-11-30
I have the plugin, and looking at the mail log it appears to be monitoring the mail, still after about 100 emails I manually marked as spam, I would think it would start to recognize at least one.

---

### Post by samiaji on 2005-12-05
Hi Guys 
I have written about this in here:

[http://ubuntuforums.org/showthread.php?p=547747](http://ubuntuforums.org/showthread.php?p=547747)

I used spamassassin and bogofilter in tandem. However you still need to train both spamassassin and bogofilter, I described everything in above posting.
Good luck!

Regards
Samiaji

---

