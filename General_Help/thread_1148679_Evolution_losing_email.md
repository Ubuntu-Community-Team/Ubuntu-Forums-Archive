---
title: "Evolution losing email"
date: 2009-05-04
forum: General Help
---

### Post by nixIT on 2009-05-04
Hello all, 

running Ubuntu 8.10 at work, and connect to our exchange server with Evolution and the connector.  

This has been working quite well until recently, maybe the last 2 weeks.

I started noticing Evolution "losing" email.  I would start evolution in the AM and notice emails I need that request a response.  By the time I would get to the emails, usually a couple hours later, I can no longer find them in evolution.  

I log into our exchange server via OWA, and bam, the emails are sitting in my inbox on the server, but not in evolution.

Is there a way to get Evolution to see those emails?  

--nixIT

---

### Post by nixIT on 2009-05-07
Anyone?

I am also experiencing other issues with Evolution, for one, when I first come to work I boot up my laptop, launch evolution, and it appears to connect to the exchange server with no problem, but when I click on a message to read it, the preview pane does not refresh, I can click on other messages and the same thing.  I let it sit on a message for 10 minutes and still nothing.  At this point I click the close X, and I am greeted with the "Not responding"/"Force Quit" dialog.  

Once I force quit, evolution will not launch anymore, I need to restart.  this used to happen once in a blue moon, but recently (maybe starting 2 weeks ago), that "blue moon" is every day.  Normally I have to reboot 3-4 times.

Is this a evolution issue?  corrupt Ubuntu install?  problems with the exchange server?

Need some help please.

--nixIT

---

### Post by nixIT on 2009-05-08
more on my evolution problem, this morning I launched evolution and it appeared to connect to the exchange server, as I could see my email, though I didn't have any new messages.  I logged into OWA and had about 12 new messages, I did a "send/receive" from evolution and nothing came in.

does anyone have any ideas?  Is this a problem with evolution, or our network/email server?

Any help is GREATLY appreciated and needed.  please

--nixIT

---

### Post by Aenima99x on 2009-05-12
Exact same issue here, it's really frustrating. I'm tired of having to use a hybrid combo of Evolution hooking in to OWA and MAPI and also actually using OWA to check my emails. It's the only thing I have left to fix after getting Pidgin to hook into our MOC/LCS. :mad:

---

### Post by nixIT on 2009-05-25
Let us know if you get that fix, I would love to get mine fixed, but I don't know where to look.

-nixIT

---

### Post by chrisstuck on 2009-05-26
Having the same problem , or similar .
Open evolution , check mail and it will show as downloading them etc then they vanish . I had an issue were only mail from one sender was not showing but it was indication unread mail but that was a letter in the search window . Changed that and then the next time bam no more mail . Going to have to ditch ubuntu if Ican't resolve this .
Chris

---

### Post by MeKino on 2009-05-31
I'm also experiencing this problem.

Evolution says it is downloading messages and then none appear in the inbox!

Over the next few days I can check for messages on the server before opening evolution. If it is genuinely losing emails I'll post back the results.

---

### Post by MeKino on 2009-06-01
I checked the server and there were 3 messages.

Evolution downloaded and 1 appeared in my inbox. The other 2 went straight into the Junk folder. There's no indication in the Junk folder of any new messages so it's quite likely that this is where some are ending up.

If you automatically delete junk on exit then they're gone forever.

Also, folder properties does not seem to show the correct number of messages - it looks like a total-to-date including deletions!

---

### Post by jgomezlu on 2009-06-01
Same problem here .. 

Had to switchback to outlook on VMware to keep working, since all the time evolution seems to left emails on the exchange inbox, and other times

Also, had problems when a follow-up of a thread came to the inbox, and the original message was move to another folder .. message content display outdated info, and not the real message (as seen on OWA).

... hope some one can fix this .. 

Best regards,
JP

---

### Post by nixIT on 2009-06-01
who do we report these bugs to?  are these issues known by the developer? I would love to keep using evolution, but as the few people on this thread confirmed, there are issues with evolution leaving email on the server and not retrieving it.

does anyone have any suggestions on what is causing this?

--nixIT

---

### Post by MeKino on 2009-06-21
I have again checked the server before downloading messages. I had 3 messages waiting, evolution informed me it was downloading them but none appeared in my inbox.

They went, instead, straight to the junk folder.

Evolution does not indicate how many (new) messages are sent to the junk folder and this is not trivial because one was a credit card statement!

I think I may use thunderbird instead...

---

### Post by lisati on 2009-06-21
I sometimes get non-junk messages sent to the junk folder automatically with Evolution, and usually indicate a need to do some retraining by clicking on "not junk".  As for the disappearing emails, I haven't actually noticed.....

There's always the option of changing to Thunderbird....

---

### Post by scabies on 2009-08-24
I've been having the 'lost email' issue in Evolution a few times this year. Mails will be in OWA but not my Inbox.

Thanks to this thread, I checked the Junk folder and there they all were. I just unchecked the Preferences->Accounts->receiving options->'check incoming folders for junk', so hopefully this will end the problem. Didn't notice that before.

Edit: Only doing the above step didn't stop evolution from filtering valid messages as junk. I found the other option in Preferences->Mail Preferences->Junk, and unchecked the 'check messages for junk' options in that tab as well. We'll see.

---

### Post by texla on 2009-08-30
> **scabies said:**
>  I found the other option in Preferences->Mail Preferences->Junk, and unchecked the 'check messages for junk' options in that tab as well. We'll see.

Wow, thanks for this fix!  Been stumped by this for a while - I actually unchecked all of the junk options since my host email already filters for this.  I had moved to Thunderbird but I really want to work with evolution because of it's calendar - which is great by the way.  Now if I can just find the 4000 emails it lost during my reinstall.... OK, well those old emails just showed up, too - this is a heck of a fix. All is good.

---

### Post by finno on 2009-11-05
Thanks for that work around!. All my incoming emails went straight to the junk folder also - I presume this is unintended behaviour?. I am working on fresh install of Karmic/Evolution and this is a serious problem when combined with the auto emptying of the junk folder. I was unable to install my trusted Thunderbird but due to this bug ttps://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/431091 I had no success.

---

