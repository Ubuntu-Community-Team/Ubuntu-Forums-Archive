---
title: "Caching Suggestion."
date: 2009-02-26
forum: Forum Feedback &amp; Help
---

### Post by drubin on 2009-02-26
I am not speaking from VAST caching experience. But from a technical point of view I understand that the forums web servers sit behind a Squid Proxy to cache any data it thinks it can.. Mostly images javascript css and such.

It then accorred to me that 99.9% of the forums are the same data and the same web pages being severed to all active users. 

The issue I noticed was in the top right hand corner. 
>  Welcome, **drubin**.
You last visited: **3 Hours Ago at 12:24 PM**
Private Messages:** Unread 0, Total 138.**


Those simple 3 words make the those almost all logged in pages uncacheable? Does this make sense is this even a valid point? I am sure you guys have thought about every single way to alleviate load from the servers and this might be something worth looking into. Maybe for logged-in users this is pointless because of session vars last update and other backend stuff. 

I would really like to hear peoples opinions about this topic.

---

