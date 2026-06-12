---
title: "Unable to log into MSN using GAIM"
date: 2006-09-11
forum: Desktop Environments
---

### Post by xwipeoutx on 2006-09-11
Hi,

I'm having issues logging into MSN using GAIM.  It connects, but then disconnects me saying "The MSN Servers are temporarily unavailable, please try again later".

I asked friends (on windows), and they're able to log on using the native client, and I can log on using webmessenger.msn.com. It worked this morning and yesterday, too...

I tried upgrading to gaim 2.0 beta 3, but I get the same error.

Any help?

---

### Post by robinl on 2006-09-11
I am using GAIM 2.0.0.beta3 and I can confirm this. I can log on on Windows no problem and aMSN works is well. This problem also affects Kopete and it seems like Microsoft stopped allowing the protocl gaim and kopete are using...

---

### Post by xwipeoutx on 2006-09-11
Gah, really? *sigh* looks like I'm using aMSN then... gaim is so much cooler :(

EDIT: Tried aMSN - same thing.  You sure it works for you?

---

### Post by kendals on 2006-09-11
Same problem for me as well. They've done something in the last 5 hrs!

---

### Post by ynnhoj on 2006-09-11
i just tried logging into my msn account with gaim, and it worked fine.  though i am running v1.5.1, not the new beta.  i would test kopete too, but i don't have it installed right now.. but considering past useage, i don't have any reason to believe that it wouldn't work perfectly fine.  i've never encountered that sort of problem.

---

### Post by rogier.de.groot on 2006-09-11
Gaim's Windows version doesn't work anymore either - at least on my WinXP box here @ school.

---

### Post by kendals on 2006-09-11
I just upgraded to gaim2beta3.1 to see if that fixed it- nope!

MS has certainly changed something! :(

---

### Post by Rios on 2006-09-11
Hmm, my Gaim on my work XP laptop works no problem logging into both MSN and AIM.  Need to check my Linux Gaim when I get home.

I think this stretches further than different versions of software though.  In our Sheffield office none of us are having any issues with any messenger variants, however none of our Derby office can access the MSN network through either MSNMessenger or Gaim.

---

### Post by moose6589 on 2006-09-11
I can confirm that this is happening to me too. In fact, I also tried to install and run MSN Messenger through VMWare, and that didn't work as well, so I suspect it's not only Gaim-related but something screwy with the MSN service itself.

---

### Post by emix on 2006-09-11
Workaround: go in the account settings and check "Use HTTP auth. method". It worked for me.

---

### Post by thesmartace on 2006-09-11
I get the same 'temporarily unavailable' message. I'm using GAIM2 beta3.

My girlfriend (using Live Messenger in WinXP on a computer about 3 feet away) can't connect either.

---

### Post by PartickThistle on 2006-09-11
You can also use Wengophone to access MSN.  I assume this uses HTTP also.

---

### Post by turbojugend_gr on 2006-09-11
I can confirm emix workaround too, they seem to have changed the method of authorizing log-in attempts. Just this for now, I don't see them not allowing other clients to use msn, all cyber-cafes and far too many users do not use 4 programs for messanging they prefer using one... So they don't ewanna loose us.... BTW: USE JABBER protocol it is OS and somewhat of a "linux" when it come to messanging.-> [www.jabber.org](www.jabber.org).

---

### Post by kendals on 2006-09-11
Using HTTP fixes it, but I don't like using it :(

---

### Post by xwipeoutx on 2006-09-11
Using HTTP doesn't fix it for me:
> Connection error from Notification server:
Reading error

I'll go back to 1.5 and see how that goes (currently on 2 beta 3)

---

### Post by xwipeoutx on 2006-09-11
Yeah, rolling back to 1.5 and using HTTP method seems to have worked.  Yay for all.

---

### Post by PriceChild on 2006-09-11
Im' on 2.0.0beta3.1 using http method and all is fine.

Wierd, tried it this morning and it didn't work, now it does :S

Btw... supposedly msn will be changing the protocol on October 15 so that only their official clients will be able to connect.

I think its extremely bad how they will make a windows and a mac client, but no linux.

I suppose while we wait for better workarounds, we can at least use webmessenger.msn.com :)

---

### Post by turbojugend_gr on 2006-09-11
> **PriceChild said:**
> 
Btw... supposedly msn will be changing the protocol on October 15 so that only their official clients will be able to connect.

I think its extremely bad how they will make a windows and a mac client, but no linux.


If that's the case then we should all go Jabber, talk your friends into it. No email needed, you just sign in so it would be easy to convince them, visit [www.jabber.org](www.jabber.org) for more info. There are many windoz clients so you won't have problems...

I know it is somehow unappropriate to suggest a protocol in this thread, but since we all are Linux users and Jabber is OpenSource messanging I believe I am forgived for this. ;)

---

### Post by sabredog on 2006-09-11
My daughter compained to me about no MSN about half an hour ago (it is 9.30pm here in West Australia and she is allowed to log in at 9pm after her homework and chores are done. GAIM did not work on her PC running XP Pro SP2 or my Dapper PC. I also tested connectivity on my wife's XP PC with the same results (GAIM/MSN). 

However she discovered web MSN worked OK. So it is certainly at Microsoft's MSN server end!

---

### Post by dmizer on 2006-09-11
using http auth worked for me too.  what is the downside of this?

---

### Post by Nikusan on 2006-09-11
> **dmizer said:**
> using http auth worked for me too.  what is the downside of this?

Slower file transfers, maybe? I'm likely wrong though.

---

### Post by RobsterUK on 2006-09-11
> **PriceChild said:**
> Btw... supposedly msn will be changing the protocol on October 15 so that only their official clients will be able to connect.

That would be incredibly irritating, do you have link where you foung this info?

EDIT: I had the same problem as others with Gaim but now it seems to be working (I didn't change anything)

---

### Post by MarioFrick on 2006-09-11
Same problem here too, Italy, no connection from this morning, now I changed to the http authentication and it works. Thanks to all! :)

---

### Post by BrokeBody on 2006-09-11
Umm... Guys, I can't find in preferences the option to change the loging with http auth?:oops: :-? lol

---

### Post by BrokeBody on 2006-09-11
OK, found it. :D lol

---

### Post by OffHand on 2006-09-11
I think they fixed it again. I was just able to log in again.

---

### Post by ramcosca on 2006-09-11
[quote=Gaim official website]MSN Crashing
August 16th, 2006 - 6:58PM PDT

Yesterday, Gaim started crashing for a bunch of people (most notably Windows users) when trying to connect a MSN account.

* Update - August 20th, 2006 - 12:32 CDT *

Gaim 2.0.0beta3.1 has been released which fixes this and other bugs in beta3. You can download it from its SourceForge file release page. [/quote]Hope they solve this mystery.

---

### Post by dmizer on 2006-09-11
> **Nikusan said:**
> Slower file transfers, maybe? I'm likely wrong though.

lol, well since file transfers via msn were so painfully slow to being with, i never used it anyway.  i was more concerned about things like security.

edit to add:
i was using gaim2 beta3.1 on dapper when i started having the connectivity problems, i moved to another ubuntu box that had ubuntu's default install ... 1.5 or some such.  it also had the problem.  but all day, i was on my fedora core box at work using gaim2 beta3 with no problems.

---

### Post by SnackySmores on 2006-09-13
I have the same problem here :( gaim stopped sending messages, tried to reconnect, but haven't been able to do so the whole day. tried amsn and it works but I like gaim better. tried that http auth thing but it didn't work.
hopefully someone can find a fix


found out how to install the latest beta & it fixed the problem
check out this post
[http://ubuntuforums.org/showthread.php?t=241236]("http://ubuntuforums.org/showthread.php?t=241236")

---

### Post by Leonivek on 2006-09-15
> **Nikusan said:**
> Slower file transfers, maybe? I'm likely wrong though.

Not sure about that, don't use it much...  But I do know that not all messages go through with the HTTP method.  I often have to copy a message I already sent, paste it, and send it again because I get a "message undeliverable"-type message... and that's annoying ](*,) cause there's a looong delay and you receive it 5 messages into the conversation, not realizing that they didn't get the one message.

I'm having the same connection issues. I haven't been able to connect to MSN the normal way for the last few days and it's pissing me off.:mad:  I'm using Kopete.

---

### Post by akshaysrinivasan on 2006-09-15
MSN seems to be working fine for me with both gaim and kopete.Wonder what's wrong there.Do you think it is country related?

---

### Post by Leonivek on 2006-09-16
Well, I can finally connect to MSN with Kopete... the only 2 things I did was run Automatix again to install updated sofware and I received an automatic update of **MoBlock** (Peer Guardian for Linux).  And lo and behold, my MSN in Kopete works again!  

I'm thinking it was a **MoBlock **issue since nothing else in Automatix could have fixed the connection problem, or it just fixed itself somehow.  Anyhow, I'm glad it's working now and I will never use HTTP method because it is so unreliable.

Whoever has connection problems, do you also have MoBlock installed?  Just curious...

---

### Post by Leonivek on 2006-09-17
I spoke too quickly... :mad: MSN still won't connect in Kopete.  It just happened to connect at that moment. ](*,)  Gaim works fine though.  I may just stick to that.

---

### Post by Leonivek on 2006-09-19
Neither Gaim or Kopete work now (without using HTTP method) with MSN.
 :mad:   ](*,)  :frown:  ](*,)  :confused:

---

### Post by Leonivek on 2006-09-20
Sorry for the multiple replies in a row... :-$

This MSN connection problem WAS because of MoBlock.  It was blocking all Microsoft ranges.  I *had* removed the blocked Microsoft ranges when I first installed MoBlock, but it reset with the latest update.

If you are using MoBlock and think this may also be the problem, don't rely on "workarounds" like the HTTP Method... **follow the steps in [this post]("http://ubuntuforums.org/showpost.php?p=1146376&postcount=25") from [this thread]("http://ubuntuforums.org/showthread.php?t=192559").**

---

### Post by Statik on 2007-01-23
Looks like the problem is back, somewhat. My wife's GAIM msn in xubuntu has stopped connecting. It displays the 'servers temporarily unavailble' message. However, she is using the same servers, same software and same internet connection as I. We never had a problem before.

Tried HTTP as well. No joy.

Statik

---

### Post by Pobega on 2007-01-23
I can get into MSN just fine from Jabber. Using the Gajim client, to be exact.

---

### Post by Ptero-4 on 2007-02-02
Pobega. A question. If I have Jabber and wanted to chat with my friends who use MSN. Can I just add their MSN ID`s to my contact list, or do I need to get an MSN account first (I don`t have one) ?

---

