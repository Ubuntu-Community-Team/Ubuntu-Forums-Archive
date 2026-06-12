---
title: "yahoo blocking pidgin ?"
date: 2009-06-18
forum: General Help
---

### Post by imlinux on 2009-06-18
i am not able to sign into yahoo using pidgin,i am not sure if yahoo is blocking pidgin.even one of my friend reported he is not able to sign into yahoo using pidgin,anyone having similar problem?

---

### Post by dragos240 on 2009-06-18
Well.... I think it might be good to request to move this to another category, not here.

---

### Post by imlinux on 2009-06-18
> **dragos240 said:**
> Well.... I think it might be good to request to move this to another category, not here.

where? i have no idea otherwise i would have posted it there.

---

### Post by RiceMonster on 2009-06-18
They may not have blocked it. I use it with msn, and pidgin has been unable to connect once or twice due to updates in the protocol, or just errors on their end. It's likely something similar.

---

### Post by Ms_Angel_D on 2009-06-18
I'm currently connected to yahoo in pidgin with no problems. Be sure to check your connection settings.

---

### Post by MyR on 2009-06-18
I can't connect to yahoo either.

---

### Post by jonobr on 2009-06-18
Mmmmm there appears to be two different experiences at play here,

Im Ibex and connecting....

Im guessing they are either  rolling out blocking of connection to their IM from non yahoo clients
or there is something going on with certain regions areas, or providors.

Maybe if you turn logging on in pidgin it may show something or the help->debug window may show its connection attempts

---

### Post by zolistir87 on 2009-06-18
Same problem here with Jaunty. Have the problem with Kopete too on openSUSE. However it work with yahoo messenger, webmessenger from yahoo and meebo. Any fix?

It would be a really low blow from yahoo if they blocked all other clients.

---

### Post by jonobr on 2009-06-18
I think someone having a problem needs to do a wireshark trace to see whats happening at a packet level or use the debug on pidgin

Just read on the pidgin help pages

> ! from behind a firewall or NAT? ¶

Your firewall or NAT is not allowing YMSG packets (packets for the Yahoo! protocol) to pass through it. You can try changing the port Pidgin attempts to connect to. Go to Tools->Edit, find your Yahoo! account, uncheck the Enabled box, then select the account and click Modify. On the Advanced tab, change the value in the Pager port field. Ports known to work are 20, 23, 25, 80, 119, 5050, 8001, and 8002. This will not work for all users, but does help many. 

---

### Post by kerry_s on 2009-06-18
yahoo's having rolling outages right now, it will pass, just be patient.
there just doing maintenance, just instead of being down for a day like xbox live, there just shifting around to certain servers.
did i say that right? what ever :D

---

### Post by SuperSonic4 on 2009-06-18
Cool, hopefully it will be ok come morning :)

---

### Post by jonobr on 2009-06-18
Rolling outages.... That would explain it.

Im just a bit annoyed they did not send a rep around to my house to tell me.

I would have given him work to do, like chop some logs, or write this response for me.....:-)

---

### Post by JDorfler on 2009-06-18
Yahoo is almost out of money.  They are having trouble replacing and fixing their servers.  If I remember correctly, (slashdot) reported that like 17% of their servers are down for the count.

---

### Post by jtpoole99 on 2009-06-18
I wish someone would've told me too.  I've reinstalled pidgin 5 times and I've almost thought about reinstalling the system until I read this post.  I actually thought that there was something wrong with my installation.  Shame on YAHOO!  They could've at least put a notice on their website about this...

---

### Post by kerry_s on 2009-06-18
> **jtpoole99 said:**
> I wish someone would've told me too.  I've reinstalled pidgin 5 times and I've almost thought about reinstalling the system until I read this post.  I actually thought that there was something wrong with my installation.  Shame on YAHOO!  They could've at least put a notice on their website about this...

lol, i did the same thing, tried different messengers & all. 
i finally just emailed them an angry email, then they actually responded, i wasn't expecting that, most just ignore it. :lolflag:

---

### Post by MyR on 2009-06-18
> **kerry_s said:**
> lol, i did the same thing, tried different messengers & all. 
i finally just emailed them an angry email, then they actually responded, i wasn't expecting that, most just ignore it. :lolflag:

and they said???

---

### Post by kerry_s on 2009-06-18
> **MyR said:**
> and they said???

see post #10, is basically what they said. you can fireoff your own if you want: [http://help.yahoo.com/l/us/yahoo/mail/classic/forms_index.html;_ylt=Agnaq.wJrdEaeD2fG0uthUYduyR4](http://help.yahoo.com/l/us/yahoo/mail/classic/forms_index.html;_ylt=Agnaq.wJrdEaeD2fG0uthUYduyR4)

---

### Post by MyR on 2009-06-18
cool. naw I don't use yahoo because no one I know uses it. so I don't really care...

---

### Post by izizzle on 2009-06-18
I was having the same problem today. Didn't really care about it too much because most of my friends use hotmail, but great to see that it was not a problem on my side.

---

### Post by MyR on 2009-06-18
I remember using the yahoo IM client 5 or 6 years ago and it was way better than anything else at the time, supporting voice chat and text color fading.

---

### Post by spcwingo on 2009-06-18
I was having this problem again last night, so I just changed the server I was using.  Instead of:

```
scs.msg.yahoo.com
```

I'm using:

```
cn.scs.msg.yahoo.com
```

No more problems since the switch.  :D

---

### Post by r6rider on 2009-06-18
> **kerry_s said:**
> see post #10, is basically what they said. you can fireoff your own if you want: [http://help.yahoo.com/l/us/yahoo/mail/classic/forms_index.html;_ylt=Agnaq.wJrdEaeD2fG0uthUYduyR4](http://help.yahoo.com/l/us/yahoo/mail/classic/forms_index.html;_ylt=Agnaq.wJrdEaeD2fG0uthUYduyR4)

> **kerry_s said:**
> yahoo's having rolling outages right now, it will pass, just be patient.
there just doing maintenance, just instead of being down for a day like xbox live, there just shifting around to certain servers.
did i say that right? what ever :D

Do you know why my windows official yahoo messenger client can connect but pidgin can't?

---

### Post by QCompson on 2009-06-18
> **r6rider said:**
> Do you know why my windows official yahoo messenger client can connect but pidgin can't?

Exactly.  This isn't just a rolling outage problem.  Official yahoo messenger client works fine for me, pidgin won't connect.

---

### Post by loell on 2009-06-18
> **r6rider said:**
> Do you know why my windows official yahoo messenger client can connect but pidgin can't?

a couple of reasons, it could be one of there servers are down in which pidgin use to connect to, Or they could be blocking clients that are using older yahoo login protocol versions.

---

### Post by loell on 2009-06-18
and i'm not yet convinced that this is entirely a yahoo server outage, as i could connect to **scs.msg.yahoo.com** with **YMSG 15 **using gyachi, while on the same server with **YMSG 13** which pidgin might be using, spits a **login fail** error.

---

### Post by Therion on 2009-06-18
> **spcwingo said:**
>  ```
cn.scs.msg.yahoo.com
```

No more problems since the switch.  :D
Thanks for that!  Solution **confirmed** (at least for me).

I had no connection to Yahoo using Pidgin (running Karmic K.) using *scs.msg.yahoo.com* but *cn.scs.msg.yahoo *works like a charm.

---

### Post by jflaker on 2009-06-18
I was just talking to the guys on IRC #pidgin.  It seems like Yahoo is changing their protocols that Pidgin is using.....to be fixed in V2.6.

Hopefully the Ubuntu repos get updated or it will be while before you can use Yahoo.

---

### Post by loell on 2009-06-18
> **jflaker said:**
> I was just talking to the guys on IRC #pidgin.  It seems like Yahoo is changing their protocols that Pidgin is using.....to be fixed in V2.6.


yep, yahoo did notified the public about this

[http://www.ymessengerblog.com/blog/2009/06/09/we%e2%80%99re-retiring-versions-60-to-75/]("http://www.ymessengerblog.com/blog/2009/06/09/we%e2%80%99re-retiring-versions-60-to-75/")

---

### Post by redmk2 on 2009-06-18
Thanks spcwingo!  The change in severs worked for me.

---

### Post by redmk2 on 2009-06-18
> **jflaker said:**
> I was just talking to the guys on IRC #pidgin.  It seems like Yahoo is changing their protocols that Pidgin is using.....to be fixed in V2.6.

Hopefully the Ubuntu repos get updated or it will be while before you can use Yahoo.

And this update will be available to Hardy users through the repos?

-Red

---

### Post by kerry_s on 2009-06-18
> **spcwingo said:**
> I was having this problem again last night, so I just changed the server I was using.  Instead of:

```
scs.msg.yahoo.com
```

I'm using:

```
cn.scs.msg.yahoo.com
```

No more problems since the switch.  :D

confirmed that fix works!

---

### Post by nandemonai on 2009-06-18
Same issue here, server change worked. I wonder though, if they're updating the protocol, how long it will be before the cn server starts kicking us too...

---

### Post by spcwingo on 2009-06-18
Probably not long, but hopefully not before Pidgin 2.6.

---

### Post by redmk2 on 2009-06-18
Exactly!

---

### Post by jcris on 2009-06-18
Just switch to the mud servers, there faster and safer.
Im using cs101.msg.mud.yahoo.com right now on Pidgin, Zinc, CenterIM, and Yahelite.

---

### Post by Wi7ahc4l on 2009-06-19
When I tried using cn.scs.msg.yahoo.com it crashed pidgin for some odd reason, but the mud server worked great and it's noticeably faster. Thanks jcris.

---

### Post by DirtDawg on 2009-06-19
Ah, thanks for the fix!

> **jcris said:**
> Just switch to the mud servers, there faster and safer.
Im using cs101.msg.mud.yahoo.com right now on Pidgin, Zinc, CenterIM, and Yahelite.

What are mud servers and why are they safer? Thanks for the tip, btw.

---

### Post by Arup on 2009-06-19
> **redmk2 said:**
> And this update will be available to Hardy users through the repos?

-Red

Add the pidgin developers ppa and you will have automatic updates to latest pidgin via [https://launchpad.net/~pidgin-developers/+archive/ppa](https://launchpad.net/~pidgin-developers/+archive/ppa)

---

### Post by Arup on 2009-06-19
> **jcris said:**
> Just switch to the mud servers, there faster and safer.
Im using cs101.msg.mud.yahoo.com right now on Pidgin, Zinc, CenterIM, and Yahelite.

Many thanks, this worked for my pidgin/yahoo connection blues.

---

### Post by jcris on 2009-06-19
YVW Glad I could help!
The way I understand is the mud servers are patched servers to fix all the exploits, like the flooders and booters and what not. I just heard that Yahoo is fixing there routing servers which is why we cant use the usual servers. Everything will prolly be back to normal in a day or 2 its hard to tell with Yahoo! A good trick to find a fast server for yahoo that works good is to use a 3rd party chat client like Yahelite or Yahaven that has the fast server search function. Both Yahelite, and Yahaven work great in Ubuntu with all options including Voice chat and Web cams. I have tutorials on setting both up at [http://beta-monkey.info/](http://beta-monkey.info/).

---

### Post by attlinux on 2009-06-19
This morning (19 Jun 2009), I couldn't connect to yahoo messenger server by using Pidgin in Ubuntu Jaunty 9.04. I used OpenDNS for my router.

I found a tweak on internet to fix this problem:

[http://forum.ubuntu-vn.org/viewtopic.php?f=61&t=1630&start=0](http://forum.ubuntu-vn.org/viewtopic.php?f=61&t=1630&start=0)

I've done those steps:

1. Open file /etc/hosts with gedit:
sudo gedit /etc/hosts
2. Add the following line to the end of hosts:
66.163.181.184     scs.msg.yahoo.com
3. Save and Close
4. Restart Pidgin
OK

---

### Post by kerry_s on 2009-06-19
> **attlinux said:**
> This morning (19 Jun 2009), I couldn't connect to yahoo messenger server by using Pidgin in Ubuntu Jaunty 9.04. I used OpenDNS for my router.

To fix this problem, I've done those steps:

1. Open file /etc/hosts with gedit:
sudo gedit /etc/hosts
2. Add the following line to the end of hosts:
66.163.181.184     scs.msg.yahoo.com
3. Save and Close
4. Restart Pidgin
OK

wouldn't that trap you to 1 server with nothing to fall back on?

---

### Post by attlinux on 2009-06-19
> **kerry_s said:**
> wouldn't that trap you to 1 server with nothing to fall back on?

Sorry for I don't know your idea and about web server technique. However, I could connect successfully to yahoo messenger server with pidgin now. Then, I want to share it for people. You could share more idea or technique problems for me?

---

### Post by peripatetic on 2009-06-19
Detailed Explanation Here:
 Pidgin and Yahoo

As of June 17, 2009, Pidgin users are having trouble connecting to Yahoo! IM accounts.  Here is a summary of the problem:

Yahoo! appears to be upgrading their servers to a new version of their software.  This new version requires a new authentication method.  The latest version of Pidgin, 2.5.6, does not support this new authentication method.  The next version, 2.6.0, will, but it has not yet been released.

The domain name that is used to connect to Yahoo! servers is "scs.msg.yahoo.com".  This domain name is actually mapped to multiple servers.  Some of these servers have been upgraded, while others haven't.  As a result, you may see intermittant failures, or you may fail every time, while your neighbor logs in successfully.  It's effectively a roll of the dice.

[http://www.celticwolf.com/useful-information/faqs/26-pidgin-yahoo](http://www.celticwolf.com/useful-information/faqs/26-pidgin-yahoo)

---

### Post by attlinux on 2009-06-19
Thank you very much ! I try to change YM server of yahoo account in Pidgin with:
cs101.msg.mud.yahoo.com
and then, Pidgin connected successfully to YM server.
[B][http://attlinux.blogspot.com/](http://attlinux.blogspot.com/)
[/B]

---

### Post by cazacugmihai on 2009-06-19
Thanks, spcwingo.

---

### Post by AlphaMack on 2009-06-19
> **jcris said:**
> Just switch to the mud servers, there faster and safer.
Im using cs101.msg.mud.yahoo.com right now on Pidgin, Zinc, CenterIM, and Yahelite.

Yet another thanks.  Works with both Pidgin and Adium.

---

### Post by sampath1 on 2009-06-19
I'm currently connected to yahoo in pidgin with no problems.

---

### Post by djysy2000 on 2009-06-19
i have the same problem with pidgin , kopete and gyache. What can be the problem?

---

### Post by Lord Noxarethor on 2009-06-19
The specific server that Pidgin connects to for Yahoo! seems down... To fix this, edit your account, and at the "Advanced" tab, in the Pager Server field enter: [B]66.163.181.189.
[/B]Then it should work ;)

---

### Post by zolistir87 on 2009-06-19
Isn't this a temporary fix? I mean won't this server go down too eventually?

---

### Post by nandemonai on 2009-06-19
> **zolistir87 said:**
> Isn't this a temporary fix? I mean won't this server go down too eventually?

Yup. Afraid so.

---

### Post by lduvall on 2009-06-19
attlinux's fix (cs101.msg.mud.yahoo.com) worked for me. Thanks one and all!

---

### Post by scrooge_74 on 2009-06-19
> **spcwingo said:**
> I was having this problem again last night, so I just changed the server I was using.  Instead of:

```
scs.msg.yahoo.com
```

I'm using:

```
cn.scs.msg.yahoo.com
```

No more problems since the switch.  :D

This worked for me, yai!!! :lolflag:

---

### Post by gradinaruvasile on 2009-06-19
Empathy and Gyachy could connect to yahoo. Pidgin and qutecom did not... until i tried that.

---

### Post by empty_spaces on 2009-06-19
Thanks spcwingo, cn.scs.msg.yahoo.com did the trick for me too.

---

### Post by bluegene on 2009-06-19
confirmed: using **cn.scs.msg.yahoo.com** as page server worked for me too.

many thanks!

---

### Post by stratcat944 on 2009-06-19
> **spcwingo said:**
> I was having this problem again last night, so I just changed the server I was using.  Instead of:

```
scs.msg.yahoo.com
```

I'm using:

```
cn.scs.msg.yahoo.com
```

No more problems since the switch.  :D
This worked for me. Thanks!

---

### Post by AoSteve on 2009-06-19
**[B]66.163.181.189**[/b] worked for me.  I'm sure there'll be more.  Usually though, pidgin usually updates pretty quickly in problems like this.

---

### Post by mhuang74 on 2009-06-19
Another confirmation that switching to *cn.scs.msg.yahoo* works for me. Running Pidgin 2.5.2 and Ubuntu 8.10 desktop from Shanghai, China.

> **Therion said:**
> Thanks for that!  Solution **confirmed** (at least for me).

I had no connection to Yahoo using Pidgin (running Karmic K.) using *scs.msg.yahoo.com* but *cn.scs.msg.yahoo *works like a charm.

---

### Post by tudor_sid on 2009-06-19
Another confirmation that switching to cn.scs.msg.yahoo works for me...but i still have a problem..

   other accounts are connecting in pidgin, but my old(default) account doesn't connect and i have the same problem..

 I am using Pidgin 2.5.2 on ubuntu 8.10 desktop from bucharest

---

### Post by ibutho on 2009-06-19
Thank you. Changing the server to cn.scs.msg.yahoo.com works fine for me.

---

### Post by mahasmb on 2009-06-19
> **ibutho said:**
> Thank you. Changing the server to cn.scs.msg.yahoo.com works fine for me.

It worked for me too! Thanks a bunch. This was an annoying problem.

---

### Post by cantormath on 2009-06-19
Confirmed,

change
scs.msg.yahoo.com
to 
cn.scs.msg.yahoo.com

This works for now.

> **Therion said:**
> Thanks for that!  Solution **confirmed** (at least for me).

I had no connection to Yahoo using Pidgin (running Karmic K.) using *scs.msg.yahoo.com* but *cn.scs.msg.yahoo *works like a charm.

---

### Post by randy78 on 2009-06-19
Here's an explanation of what's up... I found this from going to the pidgin.im site

Lot's of good info and some workarounds too

[http://www.celticwolf.com/useful-information/faqs/26-pidgin-yahoo](http://www.celticwolf.com/useful-information/faqs/26-pidgin-yahoo)

---

### Post by loell on 2009-06-19
> **randy78 said:**
> Here's an explanation of what's up... I found this from going to the pidgin.im site

Lot's of good info and some workarounds too

[http://www.celticwolf.com/useful-information/faqs/26-pidgin-yahoo](http://www.celticwolf.com/useful-information/faqs/26-pidgin-yahoo)

at the risk of asserting a little too much of what yahoo is actually [saying]("http://www.ymessengerblog.com/blog/2009/06/09/we%E2%80%99re-retiring-versions-60-to-75/"), yahoo messenger is not using a new authentication scheme, they are just retiring an older authentication scheme namely (YMSG13, YMSG14) the pidgin guys just didn't had the chance to implement YMSG15 protocol which  was running on yahoo servers for roughly 3 years now. ;)

---

### Post by MyR on 2009-06-19
confirming that it works by changing the server.  yep; confirming.  in case anyone else is wondering it's confirmed.  if you change the server as described in the previous confirmational posts then it will fix the problem. yea, roger that, no more problems confirming or logging in.  yahoo is not blocking pidgin, just restructuring some servers as confirmed earlier. this post is just to confirm. confirming again. thanks.

---

### Post by ismoke101 on 2009-06-19
> **ibutho said:**
> Thank you. Changing the server to cn.scs.msg.yahoo.com works fine for me.

:D works fine for me, but why should i change the server? what happen to the old server??;)

---

### Post by hufferd on 2009-06-20
> **spcwingo said:**
> I was having this problem again last night, so I just changed the server I was using.  Instead of:

```
scs.msg.yahoo.com
```

I'm using:

```
cn.scs.msg.yahoo.com
```

No more problems since the switch.  :D

Thank you for the fix this fix worked for me as well :) 

Conformed this morning 6/20/09

I just wish I saw this  Thread before I un installed and installed pidgin like 15 times :lolflag:

---

### Post by sisco311 on 2009-06-20
> **spcwingo said:**
> I was having this problem again last night, so I just changed the server I was using.  Instead of:

```
scs.msg.yahoo.com
```

I'm using:

```
cn.scs.msg.yahoo.com
```

No more problems since the switch.  :D

> **peripatetic said:**
> Detailed Explanation Here:
 Pidgin and Yahoo

As of June 17, 2009, Pidgin users are having trouble connecting to Yahoo! IM accounts.  Here is a summary of the problem:

Yahoo! appears to be upgrading their servers to a new version of their software.  This new version requires a new authentication method.  The latest version of Pidgin, 2.5.6, does not support this new authentication method.  The next version, 2.6.0, will, but it has not yet been released.

The domain name that is used to connect to Yahoo! servers is "scs.msg.yahoo.com".  This domain name is actually mapped to multiple servers.  Some of these servers have been upgraded, while others haven't.  As a result, you may see intermittant failures, or you may fail every time, while your neighbor logs in successfully.  It's effectively a roll of the dice.

[http://www.celticwolf.com/useful-information/faqs/26-pidgin-yahoo](http://www.celticwolf.com/useful-information/faqs/26-pidgin-yahoo)

Thanks for the fix and the explanation as well.

---

### Post by George W. Tush on 2009-06-20
The fix may be working for some, but as sure as my name is George W. Tush, the fix is not universal.  It ain't workin' for me.

If anyone has other ideas, they would be warmly welcomed.

Tush

---

### Post by SR_ELPIRATA on 2009-06-20
The server change did it for me too. I was worried about this and I knew that 3 computers couldnt be wrong :)

---

### Post by jtpoole99 on 2009-06-21
> ```
cn.scs.msg.yahoo.com
```
No more problems since the switch.  :D

This worked for me too after rebooting several times, but I'm back online with my Yahoo friends.  Thanks for this suggestion/fix.  I'm so thankful.:D

---

### Post by MyR on 2009-06-21
so you can confirm that switching to a different server solves the problem?

---

### Post by diagram30 on 2009-06-21
Confirming that the server change works.

---

### Post by Fred82664 on 2009-06-21
I think yahoo has been in bed with MicroSoft and is slowly blocking none yahoo  or nonwindows  clients GYach worked two weeks ago now it dose not

---

### Post by Softpedia on 2009-06-21
Man... this is fuc*ed up... I thought maybe it is something with the ISP, but it turns out that yahoo did it again... blocking all of our (YES, we... the Linux users (on Mac works very well)) messengers.

For anyone else out there having this problem... do like this:

1. Open Pidgin and go to *Accounts -> Manage Accounts*

[[img]http://img6.pictiger.com/9f2/18252914_th.jpg[/img]](http://img66064.pictiger.com/images/18252914/)

2. Click on the yahoo account and then on the "Modify" button.

[[img]http://img6.pictiger.com/f03/18252915_th.jpg[/img]](http://img66064.pictiger.com/images/18252915/)

3. Click on the "Advanced" tab

4. Paste the following line in the "Pager server" field:

```
cn.scs.msg.yahoo.com
```

[[img]http://img6.pictiger.com/94a/18252916_th.jpg[/img]](http://img66064.pictiger.com/images/18252916/)

5. Click the "Save" button, then click the check box in front of the Yahoo account to connect.

6. That it!

I am so mad right now on yahoo for doing this lowlife strategy on Linux users.

*Tutorial by Marius Nestor*

---

### Post by hvbakel on 2009-06-21
A new pidgin version just came out that fixes the Yahoo problems. If you follow the link on the home page ([http://www.pidgin.im/](http://www.pidgin.im/)) it has instructions on how to install it by adding a new repository.

---

### Post by Softpedia on 2009-06-21
> **hvbakel said:**
> A new pidgin version just came out that fixes the Yahoo problems. If you follow the link on the home page ([http://www.pidgin.im/](http://www.pidgin.im/)) it has instructions on how to install it by adding a new repository.

How about Kopete, Gyachi or Empathy? #-o

---

### Post by MyR on 2009-06-21
so, some servers have switched to a protocol that pidgin does not support right?  and pidgin released a fix?  hm it must be some sort of conspiracy!!!  but I'm still awaiting confirmation that switching the yahoo server that pidgin connects to solves the problem.

---

### Post by DirtDawg on 2009-06-21
> **Softpedia said:**
> I am so mad right now on yahoo for doing this lowlife strategy on Linux users.
As others in this thread have pointed out, Yahoo! is not deliberately targeting Linux useres. They are updating their servers' protocols (I think that's right) and Pidgin should work normally again after their next release.

---

### Post by DirtDawg on 2009-06-21
> **MyR said:**
> so, some servers have switched to a protocol that pidgin does not support right?  and pidgin released a fix?  hm it must be some sort of conspiracy!!!  but I'm still awaiting confirmation that switching the yahoo server that pidgin connects to solves the problem.
Yes, switching servers works perfectly.

---

### Post by peterhayscole on 2009-06-21
Hello - I am totally new to ubuntu and to user forums.  Couldn't figure out how to start a new thread, so this will have to do for now.  My question - I bought an Ubuntu machine used.  I really like it and am starting to find my way around it.  I am trying to set up myself as the adminstrator on this machine with my passcodes.  The guy I bought it from has his name and passcodes.

Thanks,

Peter

---

### Post by MyR on 2009-06-21
> **peterhayscole said:**
> Hello - I am totally new to ubuntu and to user forums.  Couldn't figure out how to start a new thread, so this will have to do for now.  My question - I bought an Ubuntu machine used.  I really like it and am starting to find my way around it.  I am trying to set up myself as the adminstrator on this machine with my passcodes.  The guy I bought it from has his name and passcodes.

Thanks,

Peter

System > preferences > user and groups.

---

### Post by Softpedia on 2009-06-21
Here a step-by-step tutorial [http://news.softpedia.com/news/How-to-Fix-Yahoo-problem-in-Pidgin-114754.shtml](http://news.softpedia.com/news/How-to-Fix-Yahoo-problem-in-Pidgin-114754.shtml)

---

### Post by ibutho on 2009-06-21
> **Softpedia said:**
> How about Kopete, Gyachi or Empathy? #-o
I tried empathy a few hours ago and I couldn't connect to Yahoo until I changed the server to cn.scs.msg.yahoo.com.

---

### Post by ibutho on 2009-06-21
> **ismoke101 said:**
> :D works fine for me, but why should i change the server? what happen to the old server??;)
Don't know for sure, but it could be that yahoo is changing their protocol and the pidgin guys are playing catch up.

---

### Post by heatblazer on 2009-06-22
> **spcwingo said:**
> I was having this problem again last night, so I just changed the server I was using.  Instead of:

```
scs.msg.yahoo.com
```

I'm using:

```
cn.scs.msg.yahoo.com
```

No more problems since the switch.  :D

Thanx that fixes it :")

---

### Post by john_navarro on 2009-06-22
[getdeb.net]("getdeb.net") now has the lastest version of Pidgin which supports the current Yahoo protocol.

---

### Post by spcwingo on 2009-06-22
2.5.7 hit the Pidgin PPA today too.  :D

---

### Post by wncben on 2009-06-23
The version of pidgin that shipped with ubuntu uses older protocols which yahoo is phasing out.  Yahoo is going server by server phasing out this older protocol.  Changing your server in pidgin is a temporary fix as eventually Yahoo will update those servers as well.
  Ubuntu does not automatically update pidgin between releases, except for security issues, but the folks at pidgin have set up a ppa which will allow it to automatically update with update manager.

 Go to [http://www.pidgin.im/download/ubuntu/ ]("http://www.pidgin.im/download/ubuntu/")

and follow the directions there.  Once you have done that go to update manager, which is located under the system>admin tabs and click on the check for updates button, which will pull up the pidgin updates and solve this yahoo problem, at least until yahoo's next update...

~Cheers

---

### Post by Sentience on 2009-06-23
> **wncben said:**
> The version of pidgin that shipped with ubuntu uses older protocols which yahoo is phasing out.  Yahoo is going server by server phasing out this older protocol.  Changing your server in pidgin is a temporary fix as eventually Yahoo will update those servers as well.
  Ubuntu does not automatically update pidgin between releases, except for security issues, but the folks at pidgin have set up a ppa which will allow it to automatically update with update manager.

 Go to [http://www.pidgin.im/download/ubuntu/ ]("http://www.pidgin.im/download/ubuntu/")

and follow the directions there.  Once you have done that go to update manager, which is located under the system>admin tabs and click on the check for updates button, which will pull up the pidgin updates and solve this yahoo problem, at least until yahoo's next update...

~Cheers



I tried it and got this.

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'echo' is not known on line 2 in source list /etc/apt/sources.list.d/pidgin-ppa.list, E:The list of sources could not be read.'



Not only did that not work but now my update manager is broken.

---

### Post by Sentience on 2009-06-23
Did I type it in wrong and screw something up? Can this be reset to defaults so it will work again?

---

### Post by SwedishWings on 2009-06-24
> **Sentience said:**
> Did I type it in wrong and screw something up? Can this be reset to defaults so it will work again?


Something went wrong, so do this:

```
$ sudo gedit /etc/apt/sources.list.d/pidgin-ppa.list
```

and make sure the contents is as follows (if you are using intrepid)
```
deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu   intrepid main
```

---

### Post by raymondh on 2009-06-24
Just downloaded the latest pidgin.

I've been using the 'cn' server that now does NOT work.  Neither will assigning the IP address work.

What worked/works for me now is the old server scs.msg.yahoo.com

---

### Post by Sentience on 2009-06-24
> **SwedishWings said:**
> Something went wrong, so do this:

```
$ sudo gedit /etc/apt/sources.list.d/pidgin-ppa.list
```

and make sure the contents is as follows (if you are using intrepid)
```
deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu   intrepid main
```

This is what it says. I am using Jaunty

echo deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) \     `lsb_release --short --codename` main | \
    sudo tee /etc/apt/sources.list.d/pidgin-ppa.list

echo deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) \     `lsb_release --short --codename` main | \
    sudo tee /etc/apt/sources.list.d/pidgin-ppa.list

---

### Post by buddhacub1120 on 2009-06-24
> **spcwingo said:**
> i was having this problem again last night, so i just changed the server i was using.  Instead of:

```
scs.msg.yahoo.com
```

i'm using:

```
cn.scs.msg.yahoo.com
```

no more problems since the switch.  :d


worked for me!!!!

---

### Post by colau on 2009-06-24
> **spcwingo said:**
> I was having this problem again last night, so I just changed the server I was using.  Instead of:

```
scs.msg.yahoo.com
```

I'm using:

```
cn.scs.msg.yahoo.com
```

No more problems since the switch.  :D
I also did this and it worked.

---

### Post by ubuntu27 on 2009-06-24
[How to: Fix Yahoo Problem in Pidgin]("http://news.softpedia.com/news/How-to-Fix-Yahoo-problem-in-Pidgin-114754.shtml")

---

### Post by MyR on 2009-06-24
so I can either change the yahoo server or update pidgin?

---

### Post by ksp1717 on 2009-06-24
It worked for me when i changed the server to "cn.scs.msg.yahoo.com"

Thanks for the post.

---

### Post by maddentim on 2009-06-24
Thanks!

---

### Post by SwedishWings on 2009-06-24
> **Sentience said:**
> This is what it says. I am using Jaunty

echo deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) \     `lsb_release --short --codename` main | \
    sudo tee /etc/apt/sources.list.d/pidgin-ppa.list

echo deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) \     `lsb_release --short --codename` main | \
    sudo tee /etc/apt/sources.list.d/pidgin-ppa.list

Remove the contents of "/etc/apt/sources.list.d/pidgin-ppa.list" and replace with 
```
deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu jaunty main
```

---

### Post by GrimJack on 2009-06-26
Hardy here. Updated to 2.5.7 by adding the appropriate repository. Connecting via scs.msg.yahoo.com.

Everything seems to work EXCEPT when a user on my list logs off, my list still shows them as being online. I have to log-off Yahoo then log back in to refresh/keep the list current.

Anyone else having this issue?

---

### Post by zolistir87 on 2009-06-26
> **GrimJack said:**
> Hardy here. Updated to 2.5.7 by adding the appropriate repository. Connecting via scs.msg.yahoo.com.

Everything seems to work EXCEPT when a user on my list logs off, my list still shows them as being online. I have to log-off Yahoo then log back in to refresh/keep the list current.

Anyone else having this issue?


I think it's a bug. It's happening to me too on both Ubuntu and openSUSE.

---

### Post by t.alex on 2009-06-26
> **GrimJack said:**
> 
Anyone else having this issue?

same here.

---

### Post by hootergrl123 on 2009-06-27
> **spcwingo said:**
> I was having this problem again last night, so I just changed the server I was using.  Instead of:

```
scs.msg.yahoo.com
```

I'm using:

```
cn.scs.msg.yahoo.com
```

No more problems since the switch.  :D

This solution worked for me perfectly!!!! Thank you!!!!

---

### Post by jaronron10 on 2009-06-28
> **ksp1717 said:**
> It worked for me when i changed the server to "cn.scs.msg.yahoo.com"

Thanks for the post.


Yep that solved the problem. 

Thanks

---

### Post by mastapat11 on 2009-07-04
> **spcwingo said:**
> I was having this problem again last night, so I just changed the server I was using.  Instead of:

```
scs.msg.yahoo.com
```

I'm using:

```
cn.scs.msg.yahoo.com
```

No more problems since the switch.  :D


this was the simplest and only working solution ive come across.
THANKS!

---

### Post by GrimJack on 2009-07-04
All of the problems I was having have been resolved by updating to Pidgin 2.5.8.

---

### Post by BlazeFire247 on 2009-07-04
I'm not sure if Yahoo! is completely blocking Pidgin, because it kept on saying "Connection Refused". 

> **spcwingo said:**
> I was having this problem again last night, so I just changed the server I was using.  Instead of:

```
scs.msg.yahoo.com
```I'm using:

```
cn.scs.msg.yahoo.com
```No more problems since the switch.  :D

This fixed it :biggrin:.

---

### Post by KeyserSoze93 on 2009-07-04
Close pidgin.

Open up ~/.purple/accounts.xml

And replace:

scs.msg.yahoo.com

with:

cn.scs.msg.yahoo.com

Open pidgin and it should connect.

EDIT: Sorry, didn't see it was solved. Could you set the title to solved to people know theres a fix?

---

### Post by MyR on 2009-07-04
> **KeyserSoze93 said:**
> Could you set the title to solved to people know theres a fix?

no

---

### Post by Kingskid on 2009-07-09
> **attlinux said:**
> Thank you very much ! I try to change YM server of yahoo account in Pidgin with:
cs101.msg.mud.yahoo.com
and then, Pidgin connected successfully to YM server.
[B][http://attlinux.blogspot.com/](http://attlinux.blogspot.com/)
[/B]

For some reason doesn't work for me.

---

### Post by alexcckll on 2009-07-10
Is the Pidgin update going to be made available to us on Hardy - so I can go grab it via Update Manager from the official Canonical repos?

---

### Post by GrimJack on 2009-07-10
> **alexcckll said:**
> Is the Pidgin update going to be made available to us on Hardy - so I can go grab it via Update Manager from the official Canonical repos?

To install the update on Hardy, follow the instructions here:
[http://www.pidgin.im/download/ubuntu/](http://www.pidgin.im/download/ubuntu/)

---

### Post by fooey on 2009-07-10
oh sweet. i've been wondering what the hell has been going on past few weeks with pidgin & yahoo. i kept thinking it was a networking issue on my end. figures. thanks for all the replies guys.. :p

> **GrimJack said:**
> To install the update on Hardy, follow the instructions here:
[http://www.pidgin.im/download/ubuntu/](http://www.pidgin.im/download/ubuntu/)

thx

---

### Post by alexcckll on 2009-07-11
> **GrimJack said:**
> To install the update on Hardy, follow the instructions here:
[http://www.pidgin.im/download/ubuntu/](http://www.pidgin.im/download/ubuntu/)
Umm - but isn't that more dangerous than just getting the enhancement in?

Canonical - please could you make this fix available through standard support processes.

---

### Post by MyR on 2009-07-11
> **alexcckll said:**
> Umm - but isn't that more dangerous than just getting the enhancement in?

Canonical - please could you make this fix available through standard support processes.

Dangerous? How?

---

### Post by alexcckll on 2009-07-11
> **MyR said:**
> Dangerous? How?
Downloading from non-standard, unsupported locations.

What happens if a change made by Pidgin breaks my machine?

---

### Post by MyR on 2009-07-11
> **alexcckll said:**
> Downloading from non-standard, unsupported locations.

What happens if a change made by Pidgin breaks my machine?

remove pidgin's repo, uninstall pidgin, then reinstall from ubuntu's repo?

---

### Post by TenPlus1 on 2009-07-11
Pop into [www.getdeb.net](www.getdeb.net) and get the latest version of Pidgin which is currently 2.5.8...  Yahoo works fine with that version...

---

### Post by alexcckll on 2009-07-12
Umm - but surely as Canonical know this is going on, wouldn't Release management roll the version that fixes it into the standard system?

---

### Post by La Man on 2009-07-31
Hi,
 
I Uninstalled the old version
Install the latest and greatest from the site 2.5.8
My yahoo connection is still NOT working
 
Any idea?
 
NOTE: I'm using WINDOWS XP
 
Pidgi Tx

---

### Post by t.alex on 2009-07-31
> **La Man said:**
> 
NOTE: I'm using WINDOWS XP

wrong forum! :lolflag:

---

### Post by colau on 2009-08-15
This was the kit!
```

cn.scs.msg.yahoo.com

```

---

### Post by aer0usa on 2009-08-27
Sweet, cn.scs.msg.yahoo.com did it! When Pidgin quit working on both Ubuntu and WinXP, I figured something was up. Too bad I didn't see this thread earlier. 
Thanks!

---

### Post by SeePU on 2009-08-29
'Didn't help me at all.  

All of a sudden, I can't use ONE Instant Messenger in Ubuntu or any Linux distro!

Why do Instant Messengers in Linux suck so badly?!?  

Even before the behavior would often be odd or unpredictable.

I thought my problems in Kopete had to do with this idea of Yahoo blocking 'other' clients.  But, I'm not sure about that now.

I am not sure what is wrong but I can use Yahoo Messenger just fine in XP. ;-/

---

### Post by brandon_h on 2009-10-02
> **attlinux said:**
> 

I've done those steps:

1. Open file /etc/hosts with gedit:
sudo gedit /etc/hosts
2. Add the following line to the end of hosts:
66.163.181.184     scs.msg.yahoo.com
3. Save and Close
4. Restart Pidgin
OK

This worked for me!

---

### Post by alexcckll on 2009-10-09
I've been scouting around and found the following..

[http://www.ymessengerblog.com/blog/2009/09/18/versions-6-7-5-will-end-on-september-30/](http://www.ymessengerblog.com/blog/2009/09/18/versions-6-7-5-will-end-on-september-30/)

I don't know what version of the Yahoo client Pidgin was functionally equivalent to.. but please could the Ubuntu release managers SRU the later versions in..?

---

### Post by adhika_rexuss on 2009-10-11
this [thread]("http://ubuntuforums.org/showpost.php?p=8084531&postcount=10") fixed my issue while connecting to yahoo messenger through pidgin.

I don't know if this is related with the link that **alexcckll** gave above.

---

### Post by brandon_h on 2009-10-12
scsa.msg.yahoo.com

worked for me

---

### Post by alexcckll on 2009-10-13
Doesn't for me.

What settings should I use for Pidgin 2.4.1?  Is the fix for Jaunty etc going to be SRUd into Hardy?

---

### Post by adhika_rexuss on 2009-10-14
Hi alexcckll, you might want to upgrade your Pidgin to 2.6.2.
Yahoo doesn't allow any clients that is equivalent to YM version 6 - 7.5 to login

---

### Post by alexcckll on 2009-10-14
> **adhika_rexuss said:**
> Hi alexcckll, you might want to upgrade your Pidgin to 2.6.2.
Yahoo doesn't allow any clients that is equivalent to YM version 6 - 7.5 to login
Granted -but is that being SRUd into HArdy and Intrepid?

---

### Post by Skara Brae on 2009-11-02
> **spcwingo said:**
> I was having this problem again last night, so I just changed the server I was using.  Instead of:

```
scs.msg.yahoo.com
```

I'm using:

```
cn.scs.msg.yahoo.com
```

No more problems since the switch.  :D
Yet another confirm with **cn.scs.msg.yahoo.com**, Pidgin finally connects.

Thank U, spcwingo (I hope you like popcorn) :popcorn:

*Whoops*, I'm (still) running Pidgin 2.4.1.
That's with Xubuntu 8.04 and Fluxbox.
Better upgrade Pidgin.
Done.

---

### Post by waynefoutz on 2009-11-16
Well I've been reading this two month old thread, I just want a client for Yahoo IM. The Pidgin repositories method doesn't work for me. Changing the server doesn't work for me. I tried installing the latest build of Pidgin from the source on my Intrepid install....it failed. 

So much for Pidgin. 

Found this page: [http://www.ubuntugeek.com/install-empathy-in-ubuntu-jauntyintrepidhardy.html#more-2566](http://www.ubuntugeek.com/install-empathy-in-ubuntu-jauntyintrepidhardy.html#more-2566)

Installed Empathy on Intrepid. Works great.

---

### Post by awaaas on 2010-06-23
I just managed to connect to yahoo! , here's the way i did it :

1. Edit Your Account
2. Click on Advanced Tab
3. Check the "Use account proxy for SSL connections"

---

### Post by MyR on 2010-06-23
> **awaaas said:**
> I just managed to connect to yahoo! , here's the way i did it :

1. Edit Your Account
2. Click on Advanced Tab
3. Check the "Use account proxy for SSL connections"

Thanks for the update.

---

