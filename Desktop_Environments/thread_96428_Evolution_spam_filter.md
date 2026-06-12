---
title: "Evolution spam filter"
date: 2005-11-28
forum: Desktop Environments
---

### Post by samiaji on 2005-11-28
After some research and adaptation I came up with personal spam filter using bogofilter and spamassassin with Evolution.

[B]Disclaimer: 
I just compiled and adapted what others have written about filtering spam, I included the reference web site at the endo of this post.
I assumed you use standard installation so every directory will be as standard. Adapt to you own situation
Make backup -- I can't strees this enough, proper backup have saved me many times. [/B]

Background:
I used Faculty of IT at UTS procmail spam filtering at server side. However since I will leaving soon I better "train" my laptop some spam filtering

Ok here is my spec
Dell Inspiron 5100 laptop wiht P4 2.8 GHz, 512 Mb RAM, 32 MB ATI 7500, 30 GB HDD
Ubuntu Breezy 5.10, Evolution 2.4.1, Spamassassin 3.0.4-2, Bogofilter 0.95-2
I used everything standard in Breezy (either cd or repo)

First install spamassassin and bogofilter if you have not done so with whatever methods you like.

First step enable Junk mail filter in Evolution
*Edit->Preferences->Mail Preferences->Junk->*Check incoming mail for junk and remote test

Second create two message filters in Evolution to utilise bogofilter
The first filter is to teach bogofilter to recognise spam email (either from  marked automatically or manually by user).

Give the rule any name mine is **Bogofilter Teach Spam**
*Set Status is Junk ThenPipe to program /usr/bin/bogofilter -s + Stop Processing*
This is how it looks:
[IMG]http://www.fe.uajy.ac.id/~ss/bogoteach.png[/IMG]
The second filter is the actual bogofilter action which (hopefully) remove spam
[IMG]http://www.fe.uajy.ac.id/~ss/bogospam.png[/IMG]
Give the rule any name mine is **Bogofilter Check Spam**
*Set Pipe to program /usr/bin/bogofilter -u Then Set Status Junk + Stop Processing*

You can stop here if you satisfied with bogofilter alone.

Then you have to train bogofilter using the first message filter (that is why the bogofilter teach is in the first position).

I have a collection of spam (700+) in spam folder (under evolution) and I used this for training both spamassassin and bogofilter.

Every spam email will be marked Junk and moved to Evolution Junk folder. You can marked every spam email you received and then it will be moved to Junk folder. I marked all the email in my Spam folder as junk.
Then I moved to  Junk folder and select all message. To train bogofilter you just need to apply filter

*Message -> Apply Filters* or *Ctrl+Y*

It took about 5 minutes for bogofilter to learn 700+ spam email

You also can train bogofilter to identify spam and non spam (ham) using this command in CLI

*bogofilter -s < /home/user/.evolution/mail/local/spam*  for spam message

*bogofilter -n </home/user/.evolution/mail/local/Inbox* for nonspam message and replace Inbox with whatever non spam folder you have in evolution

**REMEMBER your non spam folder have to be free from spam**. [I](thx dcstar for your comment).
[/I]
If you want to add another layer to that (using spamassassin) then here it is

First generate the spamassassin configuration using this website if you like me (a.k.a.lazy)  :) 

[http://www.yrex.com/spam/spamconfig.php](http://www.yrex.com/spam/spamconfig.php)

Then create a third message filter (after the first two for bogofilter above)

Give the rule any name mine is **Spamassassin 1**
*Set Pipe to program spamassassin -e  Does not return 0 Then Move to Folder Junk/Spam + Set Status Read + Stop Processing*
[IMG]http://www.fe.uajy.ac.id/~ss/sa.png[/IMG]
Again you have to train your spamassassin. I used (again) the spam folder I collected.

To train spamassassin use this command in CLI

[I]sa-learn --spam --mbox /home/user/.evolution/mail/local/spam
[/I]

The other feature of spamassassin is you could also teach them to recognise non spam (ham) as in bogofilter. I use this command in CLI

[I]sa-learn --ham --mbox /home/user/.evolution/mail/local/Inbox
[/I]
Replace Inbox with whatever non spam mail folder in Evolution.

After the three filters then you can create any filter to sort your email to any folder you like.
All incoming mail will be filtered by those 3 filters before any other filters.

I still train both my bogofilter and spamassassin, but the number of spam I received and appeared in Inbox have been reduced considerably. For illustration I received about 500-750 emails per day.

Regards
Samiaji
Reference
Bogofilter
[http://bogofilter.sourceforge.net/](http://bogofilter.sourceforge.net/)
SpamAssassin
[http://spamassassin.apache.org/](http://spamassassin.apache.org/)
Using bogofilter in evolution
[http://johnleach.co.uk/words/archives/2005/09/15/180/](http://johnleach.co.uk/words/archives/2005/09/15/180/)
Spamassassin in evolution
[http://software.newsforge.com/software/05/07/01/1521254.shtml?tid=130](http://software.newsforge.com/software/05/07/01/1521254.shtml?tid=130)
Spamassassin configuration generator
[http://www.yrex.com/spam/spamconfig.php](http://www.yrex.com/spam/spamconfig.php)

---

### Post by dcstar on 2005-11-29
[QUOTE=samiaji]After some research and adaptation I came up with personal spam filter using bogofilter and spamassassin with Evolution.
.......
Again you have to train your spamassassin. I used (again) the spam folder I collected.

To train spamassassin use this command in CLI

[I]sa-learn --spam --mbox /home/user/.evolution/mail/local/spam
[/I]

The other feature of spamassassin is you could also teach them to recognise non spam (ham) as in bogofilter. I use this command in CLI

[I]sa-learn --ham --mbox /home/user/.evolution/mail/local/Inbox
[/I]
Replace Inbox with whatever non spam mail folder in Evolution.
........[/QUOTE]
A word of warning on this "training", my Filters were set up to automatically tag certain incoming e-mails as "Junk" in Evolution.

This worked fine, but the e-mails still existed in my Inbox file, so if I used this "non-spam" training command I would be training Spamassassin to treat known junk as "ham"!

I have now modified my rule to move these file to my "Spam" folder before tagging them as "Junk" (although I don't know if this will affect the auto-tagging that Evolution does by itself).

---

### Post by samiaji on 2005-12-05
I have just tested my evolution spam filters by downloading email from my 2 gmail accounts. They had 300+ spam. I moved them from spam folder to inbox and download via pop3. The result all spam were catched by the filters.
Furthermore I retrained my bogofilter using the 400+ spam in my junk folder.

---

### Post by twowheeler on 2005-12-09
[QUOTE=samiaji]

Second create two message filters in Evolution to utilise bogofilter
The first filter is to teach bogofilter to recognise spam email (either from  marked automatically or manually by user).

Give the rule any name mine is bogofilter learn
*Set Status is Junk ThenPipe to program /usr/bin/bogofilter -s + Stop Processing*

The second filter is the actual bogofilter action which (hopefully) remove spam

Give the rule any name mine is bogofilter 
*Set Pipe to program /usr/bin/bogofilter -u Then Set Status Junk + Stop Processing*

You can stop here if you satisfied with bogofilter alone.

[/QUOTE]

Thanks, samiaji for your how to.  I am sorry to be dense but I don't understand the instructions.  :confused: 

There are two sets of fields in the filter rules, the one at the top for the "If" conditions, and the one at the bottom for the "Then" conditions.   Where do the rules you mentioned go?  Here are screenshots of what I have so far:

[ATTACH]4315[/ATTACH]
[ATTACH]4316[/ATTACH]

As you can see I don't know what to put in the "If" field of the second one.  Any suggestions appreciated.  Thanks!

---

### Post by buellman on 2005-12-11
[QUOTE=twowheeler]Thanks, samiaji for your how to.  I am sorry to be dense but I don't understand the instructions.  :confused: 

There are two sets of fields in the filter rules, the one at the top for the "If" conditions, and the one at the bottom for the "Then" conditions.   Where do the rules you mentioned go?  Here are screenshots of what I have so far:
[...]
As you can see I don't know what to put in the "If" field of the second one.  Any suggestions appreciated.  Thanks![/QUOTE]

Hi!

Have a look at [http://johnleach.co.uk/words/archives/2005/09/15/180/](http://johnleach.co.uk/words/archives/2005/09/15/180/)
There are 2 screenshots of how it should look.

Greets. Buellman

---

### Post by twowheeler on 2005-12-11
Cool.  Thanks a bunch.

---

### Post by M3ta7h3ad on 2005-12-12
Works like a beauty, trained it on about 250ish messages so far and I've already noticed a difference. (I get about 150ish a day from 3 mail accounts... did a send and recieve today, only 9 got through the filters and into my inbox.)

---

### Post by rasmusbp on 2006-01-13
Thanks for this advice. 

I've set up my evolution with bogofilter now, and spent a week or so training the filter (with approx 50 spam mails), but nothing seems to be happening. How do you make this spamfilter work without having 700 spam mails to help you (which I don't)?!? 

I recently migrated from Thunderbird, where the spam filter was super-efficient and a very quick learner, so I'm starting to regret making this move... 

Thanks!
Rasmus

---

### Post by samiaji on 2006-01-15
Dear Rasmus
Unfortunately the way bayesian spam filter works is by learning from spam and non spam. If you do not have enough spam for now, just do what I did everytime the spam filter missed a spam message. Select the message and click **Junk** icon on evolution. It will activated the first bogofilter filter on evolution. The other way around is to teach you filters with non spam message.
Hopw it help

regards
Samiaji

Btw if you use spamassassin as your second layer spam filter (after the bogofilter) you can utilise dcc and razor network. follow the instruction on this URL
[http://www.howtoforge.com/virtual_postfix_mysql_quota_courier_p4]("http://www.howtoforge.com/virtual_postfix_mysql_quota_courier_p4")

---

### Post by dcstar on 2006-01-15
[QUOTE=samiaji]
.......
Btw if you use spamassassin as your second layer spam filter (after the bogofilter) you can utilise dcc and razor network. follow the instruction on this URL
[http://www.howtoforge.com/virtual_postfix_mysql_quota_courier_p4]("http://www.howtoforge.com/virtual_postfix_mysql_quota_courier_p4")[/QUOTE]
Handy link, one thing to add to it for all of us not using IPv6 is:

sudo cdcc 'ipv6 off'

To prevent it from trying to use the stuff........

---

### Post by dcstar on 2006-01-23
Just an update on this method, my incoming Spam has dropped to almost ZERO now, and I have been checking my Filters Log files to see if any "false positives" have been occurring.

So far only one (which was a bulk e-mail) out of many (many) hundreds has been incorrectly identified as Junk.

I now only get the e-mails that I want, this setup seems to be 99.9% effective! :D :D

---

### Post by iTrendsNET on 2006-01-29
After applying all of the suggestions in this thread I have to say that my SPAM filtering within only a few days is already approaching 99% accuracy.  This is ready great as my total message intake per day generally averaged 100 legitimate messages plus around 50 to 70 SPAM messages.  

Thank you! :-D

---

### Post by dcstar on 2006-01-29
[QUOTE=iTrendsNET]After applying all of the suggestions in this thread I have to say that my SPAM filtering within only a few days is already approaching 99% accuracy.  This is ready great as my total message intake per day generally averaged 100 legitimate messages plus around 50 to 70 SPAM messages.  

Thank you! :-D[/QUOTE]
One thing for all the Evolution users using this solution is to regularly "clean out" your Junk folder.

I am in the habit now of checking it every couple of days to ensure that there aren't any messages that have been mistakenly identified as Spam (and I did find some bulk e-mails from an airline that I actually wanted - so I them marked those as "Not Junk").

Once you are sure that the contents of the Junk folder are junk, delete them and do a "Empty Trash" to purge them from your files.

---

### Post by iTrendsNET on 2006-02-09
UPDATE:  I have now used Samiaji's solution for a couple of weeks.  Things continue to get better with the the duel filtering setup.

Great job! \\:D/

---

### Post by Sutekh on 2006-02-09
Hullo.  I've set up the filters accordingly (using bogofilter) and went to my Junk folder, which is full of mail that I have marked Junk.  

Then I went to apply the **Teach** filter (which is at the top of my filter list).  When I click **Ctrl**+**Y** there is a little 'Filtering Folder ...' down the bottom left of Evolution.  

What should I expect to see happen?  

It went on for a minute or so, but junk still appears in my Inbox.  I can mark it as junk and off it goes to the Junk folder, but I thought it would be automatic.  

So back to my question, after all this has been setup, what should I expect to see happen??

(I had over 600 junk emails in my Junk folder, so I assume that should be enough to teach bogofilter?)

---

### Post by puccaso on 2006-04-08
erm, dont call me stupid ye but

but i dont even have
%user%/.evolution/mail/local/spam
it doesnt exist
now what do i do?!

---

### Post by dcstar on 2006-04-08
[QUOTE=puccaso]erm, dont call me stupid ye but

but i dont even have
%user%/.evolution/mail/local/spam
it doesnt exist
now what do i do?![/QUOTE]
"%user%" is the shell variable that picks out your current login name.

Manually replace it with your login name, or let the shell script do it for you.

---

### Post by graigsmith on 2006-04-29
i don't think the bogofilter part of this works. 

i tried it and trained mine on 900 spams. and the spams still come in and don't get deleted.

im trying spamassassin now.

---

