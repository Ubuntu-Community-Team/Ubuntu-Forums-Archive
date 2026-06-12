---
title: "Question about spiders"
date: 2009-07-14
forum: Forum Feedback &amp; Help
---

### Post by Tamlynmac on 2009-07-14
I noticed when logging in that the forum had 152 spiders. I assume this means 152 search engines are monitoring the forum?

I was amazed at the number. Does anyone know where all these spiders come from and for what purpose they monitor the forum? Obviously, Google uses the forum in their search engine for Ubuntu related searches, but what of the other 151?

I suspect it's from Ubuntu related sites, but is the information acquired form these spiders being monitored and/or should it be? Do they sign agreements and if so what do these agreements contain? 

No, I'm not being paranoid - it just caught my attention. I apologize ahead, if this information is readily available on the forum and I didn't find it.

---

### Post by Michael.Godawski on 2009-07-14
Moved to FF&H. ;)

---

### Post by koenn on 2009-07-14
every search engine spiders the web, and that web happens to include ubuntuforums.org. That's just how search engines are capable of producing a list of web sites when you give them some words and hit 'search'.

---

### Post by Elfy on 2009-07-14
At the moment there are 158 - the numbers change though.

AskJeeves(7), MSNBot(101), Google(37), Yahoo! Slurp(12), Google AdSense

---

### Post by Tamlynmac on 2009-07-14
Thank You for moving my thread to the appropriate section.

I understand the concept that search engines (SE) spider Ubuntu and other web sites. I guess perhaps my question was to vague.

I should have asked what controls (if any) are these spiders under and are there any agreements associated with them?

Obviously, based on forestpixie's response Google, Yahoo, etc. may have multiple searches going on at any point in time. Just wondered if these where under some soft of agreement with the forum or do they simply spider whatever site they choose without restriction?

For example, I may have arrived at the forum from a differt location or SE, yet any information I share on the forum may be accessed from Google or some other SE. Obviously, this is done to find and facilate requests from searches performed on that search engine. My question is - are those requests or SE's under any restrictions or agreements with this forum or is that simply internet global public domain property and free of such restrictions and agreements?

---

### Post by koenn on 2009-07-14
spiders are just like browsers : they read pages and follow links. If a spider would cay an Agent User string of 'IE' or 'Firefox', the forums would probably not even know it was a spider (same like you can let firefox present itself as IE to get to certain websites that are 'IE only')

basically : if you write something on a publicly accessible website, anyone is allowed to read it, be it me, googlebot, or anyone else, so i don't understand why you think there should be agreements about this.

From a different angle : search engines drive traffic to your side. Most people *want* spiders.  some would even be willing to pay for it

---

### Post by Barrucadu on 2009-07-14
Spiders just index everything they encounter. More frequently updated sites get spidered more often, hence the huge number on ubuntuforums. The only 'agreement' they follow is the robots.txt file (and some meta tags) which describe which content can and can't be indexed.
Of course, a server could be configured to block spiders, or serve different content or something, but that would be a bit of an odd thing to do when robots.txt exists.

---

### Post by Tamlynmac on 2009-07-14
> koenn
 so i don't understand why you think there should be agreements about this.

I think you misunderstood, I had no idea if any agreements existed or not. Much less if they should. I was only asking an innocent question.

I wish to thank everyone for your responses and I believe my question has been answered. My ignorance was the only reason I questioned. I have no agenda or alternative motive. Sometimes things are as they appear and I would not have asked the question, if I knew the answer.

Thanks Again for enlightening me.

---

### Post by lisati on 2009-07-14
You might find [this]("http://en.wikipedia.org/wiki/Robots_exclusion_standard") interesting, it describes one way of setting some boundaries for [spiders]("http://en.wikipedia.org/wiki/Web_crawler").

---

### Post by Tamlynmac on 2009-07-14
lisati

Thank you, that was good reads. It answered my questions and even provided more information then I expected.  ;)

I will spend more time reading and endeavoring to understand this topic. I do appreciate all the assistance everyone's provided.

---

### Post by jenkinbr on 2009-07-14
Ubuntuforums.org robots.txt:
```
User-agent: *
Crawl-delay: 20

```

Basically, robots that index ubuntuforums have access to anything that is availible to normal users.

---

