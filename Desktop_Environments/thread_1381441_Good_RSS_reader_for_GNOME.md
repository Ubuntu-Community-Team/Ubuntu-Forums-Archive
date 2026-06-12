---
title: "Good RSS reader for GNOME ??"
date: 2010-01-14
forum: Desktop Environments
---

### Post by FunkyRes on 2010-01-14
I just tried straw.
Asked it to subscribe to a validating feed with just 3 items currently in it. 10 minutes later while it was still "searching" the site I canceled. Clearly straw is not yet ready.

What desktop rss aggregator do y'all recommend?

---

### Post by TetonsGulf on 2010-01-14
Liferea gets a lot of use, but I personally get mine inside Thunderbird.

Check this out, might be useful:

[http://www.gnomefiles.org/search.php?search=rss](http://www.gnomefiles.org/search.php?search=rss)

---

### Post by nilarimogard on 2010-01-15
Definetly RSSOwl v2: [http://www.rssowl.org/overview2](http://www.rssowl.org/overview2)

---

### Post by bornagainpenguin on 2010-02-18
> **FunkyRes said:**
> I just tried straw.
Asked it to subscribe to a validating feed with just 3 items currently in it. 10 minutes later while it was still "searching" the site I canceled. Clearly straw is not yet ready.

I see that you are using Jaunty from your profile--straw does not work under Jaunty at all.  It works well under Hardy and Intrepid, and it is possible to get it to install in Karmic using the Jaunty deb, but I have been unable to fully test this out.

> **FunkyRes said:**
> What desktop rss aggregator do y'all recommend?

I'd like to know this too, since Straw has been removed from Ubuntu and is on its way out from Debian.  Soon it will not be possible to install it any more because of all the missing and changed dependencies.  I'm trying to find a replacement rss\feed reader that can store its articles and cache associated images with it for offline reading.  Please keep me posted if you find anything like this that works so I can finally upgrade to something more recent than Hardy Heron!

--bornagainpenguin

---

### Post by claracc on 2010-02-18
I use liferea too. I think it is enough good.

---

### Post by stinkeye on 2010-02-18
You could try Opera as your browser, and if you like it use the inbuilt
RSS feeds feature.

---

### Post by bornagainpenguin on 2010-02-20
> **stinkeye said:**
> You could try Opera as your browser, and if you like it use the inbuilt
RSS feeds feature.

Last time I tried Opera it wasn't truly an offline reader.  The text came through, but not the images.  Until Opera caches the images as well as the text it is useless to me as a feed reader.

Having said that, I just found an ePub reader that has feed reader support that could become exactly what I need!  People should give [Lucidor]("http://lucidor.org/lucidor/") a look and see if the newsroom feature will do anything useful for them!

--bornagainpenguin

---

### Post by bornagainpenguin on 2010-03-17
/Friendly bump

--bornagainpenguin

---

### Post by Pougnet on 2010-03-17
You could just use conky and make a rss feed script for it. A pic of a rss setup is here[IMG]http://www.mikesplanet.net/images/conkyrss.png[/IMG]

---

### Post by stinkeye on 2010-03-17
> **bornagainpenguin said:**
> Last time I tried Opera it wasn't truly an offline reader.  The text came through, but not the images.  Until Opera caches the images as well as the text it is useless to me as a feed reader.


Shows images and video embeds if you select "prefer Html" in the view menu.

---

### Post by FunkyRes on 2010-03-17
I use liferia but I have not tried it as an offline reader.

---

### Post by bornagainpenguin on 2010-03-18
> **stinkeye said:**
> Shows images and video embeds if you select "prefer Html" in the view menu.

But it didn't *cache* it for ***offline***.

--bornagainpenguin

---

### Post by bornagainpenguin on 2010-03-19
> **stinkeye said:**
> Shows images and video embeds if you select "prefer Html" in the view menu.

Okay I just reinstalled the application on my Karmic machine, using their PPA.  Where is this option you speak of?

--bornagainpenguin

---

### Post by stinkeye on 2010-03-19
> **bornagainpenguin said:**
> Okay I just reinstalled the application on my Karmic machine, using their PPA.  Where is this option you speak of?

--bornagainpenguin

Weren't we talking about Opera?
and
You were right it doesn't cache images.
I only have a desktop computer always connected to the net and didn't realize it wasn't caching the images.

---

### Post by brian mcgee on 2010-03-19
+1 Liferea

---

### Post by ramnarayan on 2010-03-20
Hi

This offline RSS feed reader is something i have been questing for, too, for quite a long while

However the solutions are pretty thin on the ground. But two options see available

A.) see lucidor
[http://www.ubuntugeek.com/lucidor-simple-ebook-reader.html](http://www.ubuntugeek.com/lucidor-simple-ebook-reader.html)

but then this is not available for download because
Bandwidth Limit Exceeded
The server is temporarily unable to service your request due to the site owner reaching his/her bandwidth limit. Please try again later.
Apache/2.2.8 (Unix) mod_ssl/2.2.8 OpenSSL/0.9.8e-fips-rhel5 mod_auth_passthrough/2.1 FrontPage/5.0.2.2635 mod_bwlimited/1.4 Server at lucidor.org Port 80

B) GobbleRSS
[http://gobblerss.pommepause.com/](http://gobblerss.pommepause.com/)

but if you are an ordinary user its installation is something more advanced than a night mare
[http://gobblerss.pommepause.com/install.html](http://gobblerss.pommepause.com/install.html)

***
So while no solution as yet, unless we can find lucidor*.deb somewhere

any more brilliant ideas other than moving to a 24 x 7 net connected place and maybe even joining a new job;-)

ram

---

### Post by bornagainpenguin on 2010-03-22
> **stinkeye said:**
> Weren't we talking about Opera?
and
You were right it doesn't cache images.
I only have a desktop computer always connected to the net and didn't realize it wasn't caching the images.

This would explain my confusion.  I'm trying all sorts of things in search of a solution.  I got two of them confused, I'm glad I thought of posting a screenshot otherwise we'd have been on this all week.  Yeah, the lack of offline cache of images kills the usefulness of the RSS feeds in Opera for me.  ;(

> **ramnarayan said:**
> So while no solution as yet, unless we can find lucidor*.deb somewhere

In case anyone is still interested in the Lucidor application I have just uploaded my copy of the app to Megaupload.com, I'd have done it sooner but I seriously expected the site to have come back up by now...

There is an MSI for Windows, a DMG image for MacOS, and a DEB for Linux.  All three platforms are zipped together for easy one stop shop downloading.  I hope this helps someone, as I recalled seeing a post somewhere last night commenting on the app but unable to download it...I just don't remember where I saw it.

Happy downloading: [http://www.megaupload.com/?d=HE5OOCQD](http://www.megaupload.com/?d=HE5OOCQD)

> **ramnarayan said:**
> This offline RSS feed reader is something i have been questing for, too, for quite a long while

I'll be giving the JAVA app you linked to in the other thread a try and post back on whether or not I have any success with it.  Sad that we're left with applications from 2005 and 2006 to do such a (seemingly) basic task, isn't it?

--bornagainpenguin

PS: The software was GPL so I don't expect any issues from uploading this software here, but nevertheless I plan to remove the link once the site comes back.

---

### Post by bornagainpenguin on 2010-03-22
> **brian mcgee said:**
> +1 Liferea

Liferea is useless and not as advertised.  Pardon me for being "ideological" about it, but if your application doesn't display text AND images from a feed I'd hardly think you could describe it as being offline capable wityh a straight face.  Words like...dishonesty... come to mind.

--bornagainpenguin

---

### Post by brian mcgee on 2010-03-22
> **bornagainpenguin said:**
> Liferea is useless and not as advertised.  Pardon me for being "ideological" about it, but if your application doesn't display text AND images from a feed I'd hardly think you could describe it as being offline capable wityh a straight face.  Words like...dishonesty... come to mind.

Uhh... I just said "+1 Liferea"

OP wanted an RSS reader recommendation... I use Liferea and like it, so I recommended it. I never claimed it was "offline capable". Sad that something as innocuous as  "+1 Liferea" would be flamebait here... yikes!

---

### Post by bornagainpenguin on 2010-03-22
> **brian mcgee said:**
> Sad that something as innocuous as  "+1 Liferea" would be flamebait here... yikes!

Sorry for jumping on you like this.  Unfortunately every time I've started a thread asking for feed reader recommendations (and specifying I seek offline reading) people keep posting Liferea and insisting it is offline capable.  I apologize for jumping all over you.

--bornagainpenguin

---

### Post by brian mcgee on 2010-03-23
> **bornagainpenguin said:**
> Sorry for jumping on you like this.  Unfortunately every time I've started a thread asking for feed reader recommendations (and specifying I seek offline reading) people keep posting Liferea and insisting it is offline capable.  I apologize for jumping all over you.

No hard feelings. Anyway, I was responding to OP. Also, I'm still happy with Liferea! :P

I've also liked RSSOwl -- not sure about caching features there... GL

---

### Post by bornagainpenguin on 2010-07-26
Just in case anyone cares can I just toss in a recommendation to give [Naufrago!]("http://www.gnomefiles.com/app.php/Naufrago!") a try?  It is much like my old favorite Straw, which is unfortunately no longer maintained these days, but seems much faster at what it does.  Best of all for me is that it does offline caching of articles and their associated images so I can still read the entire article even in areas where there is no internet available!

--bornagainpenguin

---

### Post by proxess on 2010-07-26
Google Reader. Very good, bundles of features, no need fancy client software, works on any OS.

---

