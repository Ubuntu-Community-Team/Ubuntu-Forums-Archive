---
title: "Asterisk phone system"
date: 2009-04-03
forum: General Help
---

### Post by Linux&amp;Gsus on 2009-04-03
Hi all,
got a few questions about Asterisk PBX. ("few" haha, I guess it'll be a bit longer... :D ) This is something totally new to me, and I would appreciate any fool prove, simple to understand input on this. I might not even get all the terminology right. Fell free to correct me on this so that I can learn about things.

So, I have a dream about the *"perfect"* phone system (well, ya, I know, that doesn't exist, but I can dream, ey... ;) ). Well, OK, it's *"MY"* dream, I don't know if that even would make sense or could be done better or something is impossible.
Anyways, one of my biggest issues is that I actually don't have any clue about phones. I buy them, plug them in, and start using them. I know that the phone at home is a bit older and not suitable for VoIP. But that is really not the point right now. At the moment I really don't care so much about having "the right hardware phone" for that.

**Basics**
So, to start with I would like to do the following:
I have a (older) server at home and would like to try and set up an Asterisk system on there. For the sake of "just" playing with it I don't care about a "real" phone. Means, only using Softphones on the computer, for now anyways.

So, from my understanding to actually make it work I need a VoIP provider, right? Now, is that important where this provider is located. As in, has it to be a provider in my country? E.g. in case I make most phone calls to a country other then I currently life in. Also would mean that people there could call me for local rates rather than e.g. over-sea rates. Or even better, can I set up my system in a way that I can choose between 2 or more provider or would that require 2 separate systems? If that would make sense from a cost perspective, anyways.

I've no clue how much it actually costs in the first place. If it even makes sense to "play around" with that. Means, does it cost to subscribe to a provider like with traditional telecommunication services, or is subscription free and it's a cost per call/call duration.

**Connect multiple Asterisk and/or SIP?**
I've been reading that it's possible to connect 2 (or more?) locations together to give them the same set of phone extension. So, if I got that right than if I have, say, 2 offices in 2 different cities they can call each other like on the phone system within 1 building and also forward calls from office A to office B.

How does that affect cost? What if these office are in different countries? Or does that mean that I can call from one such a location to another for free? Is that like a call via SIP or using Skype?

If so, could I then just call any SIP number for free, if e.g. a few friends have a Asterisk system or another SIP system? Asterisk is working with SIP, right?

**Who can have access to the system?**
Which also leads me to the question, can I give other people access to my Asterisk system or can I access it from remote (e.g. via VPN) and make phone calls? Also, wouldn't that mean that it could be hacked that way and someone could make a phone call I'll have to pay for? Or do I miss something here?

**Emergency calls?**
If I remember that correct then with Skype you can't make calls to emergency services, or at least they don't guarantee that this will always work. Same goes for Gizmo5. Is that possible and guaranteed to work with Asterisk? If the internet connection is up, of course.
Internet and phone lines can be down, that's not the point here.

**Fax**
Is it possible to send and receive a Fax via computer? E.g. having all even numbers as phone extension and the following odd number as Fax extension. So, something  like:
ext 10 - Phone Person A
ext 11 - Fax Person A
ext 12 - Phone Person B
ext 13 - Fax Person B
ext 14 - Phone Person C
ext 15 - Fax Person C
etc.

Sometimes having a Fax available is just handy. But I don't like the hardware Fax machines. I would like to receive a Fax on a computer as a picture or PDF document. Same with sending a Fax, instead of printing it out and then going over to the Fax machine I would prefer to do all that directly from the computer.

**System integration**
Is it possible to integrate the phone book into an existing address book? E.g. I'm using Kontact [COLOR="Blue"](Yes I use KDE ;) may the blue force be with you :D )[/COLOR] for email, calendar, RSS, etc. I'm not aware of a add-on for Kontact to make phone calls, e.g via an Asterisk system. But I really don't like the idea to add another application that is creating and using its own address book. And I then have to add or change a address at X number of apps to have everything up-to-date. That sounds like a real pain to me.
Not even to speak about sharing an address book across the network. That would be sweet as...

**Conference and video calls**
Is it possible to make conference calls? I assume within the system it's rather easy? But what about with different outside locations? E.g. having a few family members or a bunch of friends on the phone at the same time?
And how about Video calls, is that possible. And how about conference video calls?

**Hardware**
I read about the possibility to buy special hardware for an Asterisk system, rather than using a computer. So, my question is how much system resources does such a system need under which circumstances? I guess it depends mainly on how many simultaneous phone calls are to be expected.
What is better, a piece of "Asterisk hardware" or a server that is setup for it? Is RAM or CPU more likely the limiting factor? HDD space only matters for an answering machine, I guess. What is more/better/faster/easier scalable?

Is it possible to use multiple computers and load balance it for bigger systems? From which size on would that make sense?
Of course, this isn't really importing for me playing around with it and I don't plan to start up a business with 5000 employees tomorrow. However, if I played around with it and it works just fine then I might suggest something like that for our office (with 15 people) here. But for now this is simply a question out of pure curiosity.

**How-To?**
Last but not least, is there any easy to understand, fool prove, idiot safe, how-to around? So far I haven't found anything that falls into that category. But as usual, I might look at the wrong places and search with the wrong search terms.

So, I know that what a very long post. And I guess I'll have some more question in future. Unless I asked all that can be asked at once. Who knows.
Thanks for reading, and any input to increase my knowledge.

Cheers, ):P
L&G

---

### Post by Linux&amp;Gsus on 2009-04-08
Everybody knowledgless about this topic? :( (I love creating new words, can you tell? ;))

Really would appreciate some input/help/ideas/what-ever-is-helpful-to-know.

Cheers,
L&G

---

### Post by Linux&amp;Gsus on 2009-04-12
bump.

Don't want to believe that no one here knows at least *a little something* about Asterisk. :cry:
Please make smart... :)

---

### Post by haydeniv on 2009-05-01
It's not so much that there isn't asterisk experts out there.  It's more along the lines that this is an Ubuntu forum not an asterisk forum.  I really don't know anybody that tries running asterisk on an ubuntu system even though I'm sure it will work. Just really hard to configure.

You have a lot of very complicated questions that don't have simple answers.

The best answer that I can give you is some references to some voip web sites.

[http://www.voip-info.org]("http://www.voip-info.org")

[http://www.asterisknow.org]("http://www.asterisknow.org") Pre packaged phone system.  Insert CD wait 30 minutes run phone system.

[http://www.trixbox.org]("http://www.trixbox.org") Just like AsteriskNow

[http://www.vitelity.com]("http://www.vitelity.com") VOIP service provider with local DID termination

[https://www.teliax.com]("https://www.teliax.com") VOIP service provider based in Denver Colorado.

Couple of quick notes.
Bridging two offices together is a very advanced configuration.  It took me over 6 months to get mine set up properly.

Faxing over VOIP is flaky at best.

Most VOIP providers have fees with them.

You'll have much better luck posting your questions in the AsteriskNow and Trixbox forums.

All of your questions have been answered before.  Google is my friend.

---

### Post by Linux&amp;Gsus on 2009-05-02
Thanks for the links, will work though them.
Hmmm, I didn't think that it's exactly easy to setup, as in install 20min configure, ready. But I wouldn't have thought that it's so complicated and hardly anyone is doing that around here.

Well, anyways. Thanks for the help. I'll dig a bit into it and see if that's something for me to do.

Cheers,
L&G

---

### Post by craigkeiths on 2010-01-28
> **Linux&Gsus said:**
> Thanks for the links, will work though them.
Hmmm, I didn't think that it's exactly easy to setup, as in install 20min configure, ready. But I wouldn't have thought that it's so complicated and hardly anyone is doing that around here.

Well, anyways. Thanks for the help. I'll dig a bit into it and see if that's something for me to do.

Cheers,
L&G

I agree with haydeniv. There are lots of asterisks forums out there. And more people here talks about Ubuntu. You can check forums like this one: [www.asteriskguru.com](www.asteriskguru.com) for more information about setting-up your asterisk.

---

### Post by t4thfavor on 2010-01-28
I have a few asterisk systems under my control, and currently they use trixbox CE. I an lazy, and it is very easy to setup and configure. 

I can pretty much answer all of your questions (from above) But I'm lazy, so I will touch on the ones I feel are most important.

Basics
Asterisk has extensions, and trunks.
Trunks let you place calls onto another network such as the PSTN or "regular phones" Extensions allow you to hook phones to the system that are addressed by a local number like 1000.
You can call extension to extension without a voip provider, even if the extensions are across globe. This will of course be limited by your bandwidth.

Most providers will allow you a number in any place that they have a "Rate Center"

All of the ones I used are on what is called the Level Three network which is global. 

[www.cordiaip.com](www.cordiaip.com)
[www.bandwidth.com](www.bandwidth.com)
both around 20USD/month for unlimited minutes, and E911 (us)
Connecting two PBX's

Yes, there are a veriety of methods to hook them together
Physical analog connections with apropriate fxo/fxs cards, SIP, IAX2, DAHDI, and I think a few more. With this you can setup a trunk to llow users at site A to call users at site B by dialing a local extension.

Access to the system:
Whoever you give an extension, or whoever cracks you passwords.

There are some crackers out there who want free phone calls, just be advised.
and if you have a trunk with incoming, anyone who can dial a phone can call you. Just not make calls on your system unless you want them to.

Emergency:
Works via E911 in the US where they keep the main address on file. I know however that it does work, as long as you have your plans setup correctly.

System integration:
Yes it's open source.
No, Its complicated.

Fax:
Inbound you can have the system detect the tones, so I can use my regular phone number for both voice and fax, it works just fine if you have good low latency bandwidth.

outbound, forget it for the most part. There is T38, but whatever.

Hardware:
It will run on anything, it's all about call volume. 
I had trouble with it on VM's due to the lack of a hardware timer.
I have run it on a Linksys WRT54G, and the latest Quad core Xeon with 8GB ram (don't ask).

Howto:
[www.trixbox.com](www.trixbox.com) Good beginner distro for first time setup, also works well for honest deployments, fairly stable, and has regular updates.
to install and configure it from the CLI is a nightmare as there are like 50 config files, and each has a whole lotta lines.

Anything else?

the above posts had a bunch of great sites for asterisk info.

---

### Post by Tux+ on 2010-01-28
I would also look into [FreePBX]("http://www.freepbx.org/") as it gives you a GUI and installs along side other apps so that your server isn't just a dedicated PBX. Only issue with this is that you have to do more configuration and make FreePBX and Asterisk work together.

---

### Post by srt4play on 2010-01-28
Trixbox CE is a nice asterisk distribution, very easy to setup and maintain.   For a dedicated PBX I use a M350 enclosure with Intel BOXD945GCLF2 board.  It runs fine.

---

