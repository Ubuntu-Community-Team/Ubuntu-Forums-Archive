---
title: "Trimming RAM usage with Firefox v1.5?"
date: 2006-02-18
forum: Desktop Environments
---

### Post by Zeroangel on 2006-02-18
I noticed that Firefox seems to take up enormous amounts of RAM. It tends to be 100MB on startup but visiting a few webpages (ie: simply posting this with no additional tabs open) boosts that up to the realm of 170MB to +200MB.

This is not normally a problem when I performing basic operations (ie: checking email, surfing, media) but really becomes an annoyance if I am running an app that requires all of my memory to run at a decent speed. And, ie: I want the convenience of having a browser open at all times.

Is there a way to reduce firefox memory usage down to a more reasonable amount?

---

### Post by dcstar on 2006-02-18
[QUOTE=Zeroangel]I noticed that Firefox seems to take up enormous amounts of RAM. It tends to be 100MB on startup but visiting a few webpages (ie: simply posting this with no additional tabs open) boosts that up to the realm of 180MB to +200MB.

This is not normally a problem when I performing 'basic sex' (checking email, surfing, media) but really becomes an annoyance if I am running an app that requires all of my memory to run at a decent speed. And, ie: I want the convenience of having a browser open at all times.

Is there a way to reduce firefox memory usage down to a more reasonable amount?[/QUOTE]
Hmmm, a few more tests on my system show my FF 1.0.5.1 using up more memory as other tabs are opened, but it does seem to release it once those tabs are closed.

Currently firefox-bin is using 110.5 MiB just with this one forum tab in use.

---

### Post by Zeroangel on 2006-02-19
Success! I finally Googled it up and found the [following article](http://www.linuxpipeline.com/showArticle.jhtml?articleID=175007517&pgno=5).

According to the article, Firefox does a LOT of memory caching of recently visited pages in order to increase back/forward button speed.

Following those steps I have managed to trim firefox memory usage down to 70MB at startup to 118MB just to get to this page.

It is actually quite an excellent article. I suggest that you read it from [Page 1](http://www.linuxpipeline.com/showArticle.jhtml?articleId=175007517&pgno=1)

---

