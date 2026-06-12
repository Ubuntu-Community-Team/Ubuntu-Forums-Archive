---
title: "Evolution problems???"
date: 2007-06-29
forum: Desktop Environments
---

### Post by rabideau on 2007-06-29
I have noticed a number of posts with similar complaints but no responses... so perhaps I shouldn't ask this, but I will anyway.

I am trying to make evolution work as my email client however, I am unable to place reply signatures where I want them ... before the quote.  I can make quotes go out as attachments (a nice way to annoy recipients, I think...;)) I can not send quotes (another great way to make friends...) or I can have my signature be invisible and buried at the end of all quotes (just another brilliant option :().  I know all the reasons for these options however... most people in the world expect my signature to come after my text (I know that MS set the tone on this oddity).  

SO has anyone hacked or found a hack that addresses this issue????

Thanks (oh and I apologize for the sarcasm...:popcorn:)

---

### Post by bapoumba on 2007-06-30
Is this related to your problem? Please check the thread, there is a link to a bug report in it.
[http://ubuntuforums.org/showthread.php?p=2230991]("http://ubuntuforums.org/showthread.php?p=2230991")
(Personal note: I prefer my sig after the quotes, may be because I've always been used to have it that way).

---

### Post by rabideau on 2007-07-01
So here is what I have uncovered thus far with respect to Evolution...[LIST]
[*]Spamassassin or similar does not function out of the box a special set of file edits is required to make it operational. See: [https://bugs.launchpad.net/evolution/+bug/4472](https://bugs.launchpad.net/evolution/+bug/4472)
[*]Along the installation side of things there is a good tutorial on how-to integrate spamassassin into evolution at: [http://www.debianclan.org/index.php?option=com_content&task=view&id=100&Itemid=38&lang=en](http://www.debianclan.org/index.php?option=com_content&task=view&id=100&Itemid=38&lang=en)
[*]Signatures appear where the developers of evolution want them... not where users want them
[*]There is no way to customize the theme or skin
[*]Spamassassin does not start automatically, you need to Modify System>>Administration>>Boot Up Manager to make certain it runs at startup.
[*]You need to train several hundred spam and also set Evolution Edit>>Preferences>>Mail Preferences>>Junk to allow spamassassin to run
[*]mail-notification works if it is installed using **synaptic, **everything else I tried to get the mail-notification installed failed
[*]smileys appear to be broken on feisty (there's a bug report on LaunchPad)
[*]Currently I am unable to add Contact Certificates (security items)[/LIST]And perhaps most frustrating... I have found nowhere where I can contribute thoughts to improve evolution... sad, methinks.:(

I'll add my learnings as they happen....

---

### Post by bapoumba on 2007-07-01
For contributing to evolution, I have looked around. GNOME has a [forum with a devel section]("http://gnomesupport.org/forums/index.php") you might want to check. Also, all the old links from several years back regarding evolution devel now go to the Novel site. Did not find any info there, but may be I did not look enough...

I went around the spam issue using gmail account and filter. I know this is not a fix or what you are looking for. I tried to work out the spamassasin issue with a friend some time ago, he ended up going back to thunderbird.

I tried mail-notification some time ago. I dropped it.

One big issue to me is that evolution does not handle proxies. When at work (this is a laptop) I am behind a proxy, and I have to go to gmail webmail. That also should be worked out.
F1 does not start the help file! I do not need it, but for all the new people trying it out, not so friendly. There is a bug report.

I'm still sticking with it because lots of people use it, and I can help them. Thanks for your input :)

---

### Post by rabideau on 2007-07-02
Okay so in the been there done that category...

I am returning to Thunderbird.  There are simply too many gotchas in Evolution to make the effort worthwhile.  The final straws for me were:

Toolbar seems unchangeable and the spam arrangement is simply too strange and inflexible in terms of teaching inline... no right click or icon click to flag an email as spam (once you select a spam tool like spamassassin)  The native junk mail feature in evolution seems all but unteachable.

I guess I have to agree with a quote I saw from Mark Shuttelworth we need tools with good clean UIs and evolution is just not there.:(  I wish it were....

---

### Post by bapoumba on 2007-07-03
Oh well... yeah. When I have a little time, I'll set up thunderbird :)

---

### Post by rufus01 on 2007-07-12
My Evolution has frozen.  I was getting my e-mail, and it froze.  When I tried to close it I got the message, "your inbox is not responding..."  I had to force quit.

My main concern is my contacts and my older messages which I have no access to.  I read that I can sign on as a different user and get Evolution again, but what about my contacts and  organizer? Do I have to start all over again and give up my old contact list and forget about my old e-mail messages?  Does anyone have a solution?

Thanks

---

