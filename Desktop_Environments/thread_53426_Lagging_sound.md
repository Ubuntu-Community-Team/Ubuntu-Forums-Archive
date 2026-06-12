---
title: "Lagging sound"
date: 2005-07-31
forum: Desktop Environments
---

### Post by sebdah on 2005-07-31
Hi!
I've just converted from Ubuntu to Kubuntu. But when playing music with amaroK  or JuK for example my sound is lagging. Acctually / often it seems like the sound disappears in special parts of the songs. The parts where the artist is singing a bit higher (not louder) - but I'm not 100% sure that this is the case everytime..

Anyway, does someone have a suggtion to a solution?

EDIT: The sound works normally with XMMS.

Greetings
Sebastian Dahlgren

---

### Post by varunus on 2005-07-31
This is due to the fact that KDE uses the arts sound server to produce sound.  arts, in my opinion, is terrible.  You can tweak its settings from the control center and try to get better sound.

---

### Post by samuraisam on 2005-07-31
[QUOTE=sebdah]Hi!
I've just converted from Ubuntu to Kubuntu. But when playing music with amaroK  or JuK for example my sound is lagging. Acctually / often it seems like the sound disappears in special parts of the songs. The parts where the artist is singing a bit higher (not louder) - but I'm not 100% sure that this is the case everytime..

Anyway, does someone have a suggtion to a solution?

EDIT: The sound works normally with XMMS.

Greetings
Sebastian Dahlgren[/QUOTE]
 ```
sudo apt-get install amarok-xmms
```

That's what you want. Then switch the engine from (whatever) to xmms in the amarok settings.

-Sam

---

### Post by sebdah on 2005-08-01
Thank you!

Your answers led me right. For others here is what I did:

```
sudo apt-get install amarok-xine amarok-engines
```

And changed the engine in amaroK.

Thank you!

---

### Post by jfd5xte on 2005-09-02
disclaimer: I am completely new to ubuntu/kubuntu, and it's been years since I used debian as well.

I noticed that, on MY system, /usr/bin/artsplay will play uninterrupted sound in wav, ogg, and flac formats very nicely, but not mp3!!

BTW, I also (unnecessarily, imho) wasted a LOT of time searching for a source for the lame encoder. I finally found an unsigned one at:

deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main

I'm rather confused (read: annoyed) as to why I should be forced to either compile the source myself or seek out an untrusted source for such a common utility as lame. I can only guess that either lame has gone out of fashion without me realizing it, or the Kubuntu people are a lot more concerned about the mp3 patent issue than I am. 

Anyway, encoding my own new mp3s didn't help me out like I hoped, and mp3s are still VERY choppy when played by artsplay, but not when played by XMMS. I also spent time assuring that my hard drive dma settings were good, and that my artsd settings in KControl (including the setuid root bit on artswrapper) were also as they should be.

I would just like to find out if these symptoms are consistent with the other people experiencing these problems. In the past, I have had good success with artsd and I'm trying to figure out what's different now. Since arts seems to play the other formats well, and (to me) it seems very strange that lame isn't included in the standard kubuntu distribution, I'm wondering if maybe there is some level of mp3 support required by artsd that Kubuntu isn't providing by default. Any other ideas? Please don't recommend that I switch Amarok over to another engine. That may work for you, but I would like to know what's wrong with arts, and how to fix it.

Thanks!!
-jf

---

### Post by incinerator on 2005-09-02
Well, obviously you have been looking for lame in the wrong places. If you'd read the  [ubuntuguide](http://ubuntuguide.org/#codecs) you would have found out that you don't need the marillat repo. [Hoary-Extras](http://backports.ubuntuforums.org/) has everything you need.

As for the choppy sound, arts is broken and the people in charge know it. It will go away. Meanwhile, use something else. I am using the xine-engine in amarok.

To improve your technical understanding a wee bit: arts doesn't care what audio format you use. arts is a sound server, a middleman between the application and the sound driver. That saves developers the extra work of writing interfaces to every possible sound driver system for each operating system. artsplay is just a frontend to it. The libraries used to decode the various audio formats are NOT part of arts.

---

### Post by jfd5xte on 2005-09-02
Thanks for the link to the guide. I'm sure it will be very helpful for future questions I have. Interestingly, I thought I tried Hoary-extras without success, but I'll have to check it again tonight.

Do you know which mp3 libraries arts draws from? I know you say arts is broken, and maybe it is, but I'm just trying to understand specifically what's wrong. If I want to play mp3s right now, I can just use xmms (or, as you say, install another amarok engine). Unfortunately, arts works sometimes and sometimes it doesn't, and I'm trying to figure out what causes it to fail.

AFAIK, kde won't be dumping arts before KDE 4 which is still a long ways away. So to me, since arts is integrated into so much of kde, it would be nicer to get arts working again than find a workaround for every app.

---

### Post by f1dave on 2005-09-02
Afaik, the developers know of it and have called for patience. It's not something that is particularly killing my experience at the moment anyway, so I'm not too fussed.

---

