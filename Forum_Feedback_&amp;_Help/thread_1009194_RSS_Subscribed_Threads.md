---
title: "RSS Subscribed Threads"
date: 2008-12-12
forum: Forum Feedback &amp; Help
---

### Post by tdrusk on 2008-12-12
I really want an RSS feed that shows me when my subscribed threads have been updated. Every time I post in a thread it subscribes me to it, so I can keep up with my posts.

I tried adding ```
external.php?type=RSS2
``` to my subscriptions so it looks like 
```
http://ubuntuforums.org/usercp.php/external.php?type=RSS2
```. This doesn't look the way I want it. 
I also tried to use Firefox's Bookmarks>Subscribe to This Page but that doesn't bring up the right threads. 

Is there any way I can do this?

---

### Post by drubin on 2008-12-12
> **tdrusk said:**
> I really want an RSS feed that shows me when my subscribed threads have been updated. Every time I post in a thread it subscribes me to it, so I can keep up with my posts.

I tried adding ```
external.php?type=RSS2
``` to my subscriptions so it looks like 
```
http://ubuntuforums.org/usercp.php/external.php?type=RSS2
```. This doesn't look the way I want it. 
I also tried to use Firefox's Bookmarks>Subscribe to This Page but that doesn't bring up the right threads. 

Is there any way I can do this?

You cant do this. :( 

[http://ubuntuforums.org/showthread.php?t=982992](http://ubuntuforums.org/showthread.php?t=982992)

Doesn't answer your question 100% I am still trying to find the thread where this has been discussed before.

---

### Post by Dr Small on 2008-12-12
Since vBulletin doesn't send you any more emails from your subscribed thread until you have viewed the thread, I don't think this is possible.

---

### Post by drubin on 2008-12-12
> **Dr Small said:**
> Since vBulletin doesn't send you any more emails from your subscribed thread until you have viewed the thread, I don't think this is possible.

How do emails relate to RSS?

I assume this is because else you would receive tons of emails firstly your inbox would be flooded and secondly the load on the mailservers would just be intense

---

### Post by jenkinbr on 2008-12-12
I would love to see this idea implemented - I could then use feeds to subscribe to threads, and only would need to visit the thread when there is actually something I want to save.  This could funtion in a similar manner to the way the archive function of the forum works, only the RSS feeds would be realtime (or near, anyways)

The feed could function similar to this page:
[http://ubuntuforums.org/archive/index.php/t-58313.html](http://ubuntuforums.org/archive/index.php/t-58313.html)

It appears that this was availible in the past, but I'm doing more looking...

---

### Post by bapoumba on 2008-12-13
When you subscribe to a thread, the email you receive is only for the first reply given after you logged out. Other replies do not trigger emails until you log back in.

As far as sending everyone a notification (via rss or emails) for each new post, even only for subscribed threads, I cannot imagine what additional load this would represent for the servers.

---

### Post by drubin on 2008-12-13
> **bapoumba said:**
> When you subscribe to a thread, the email you receive is only for the first reply given after you logged out. Other replies do not trigger emails until you log back in.

As far as sending everyone a notification (via rss or emails) for each new post, even only for subscribed threads, I cannot imagine what additional load this would represent for the servers.

It would have to send out email to every user that has subscribed (with emails) every single time a post is mad. as apposed to once per logged out session.

Imagine a few very active threads that have subscription via instant email. ie the Bumpthread the mail servers would be in over time... (this is an extreme case). 


I thought about the emailing part as well and then worked out my inbox would be flooded.

As for the RSS this is triggered by when the client requests the RSS so I do not see this as an issue. I am actually very for this.

The only major change this would mean is that to subscribe to a thread the authentication model would have to change slightly. 
1) RSS You aren't logged in to view ie no session on the server
2) Some sort of auth token would have to be passed to identify and correctly validate this user
3) These urls *choice of user here* be shared or not..

But I am totally for it if there is a plugin or something.

---

### Post by Dr Small on 2008-12-14
> **drubin said:**
> It would have to send out email to every user that has subscribed (with emails) every single time a post is mad. as apposed to once per logged out session.

Imagine a few very active threads that have subscription via instant email. ie the Bumpthread the mail servers would be in over time... (this is an extreme case). 


I thought about the emailing part as well and then worked out my inbox would be flooded.

As for the RSS this is triggered by when the client requests the RSS so I do not see this as an issue. I am actually very for this.

The only major change this would mean is that to subscribe to a thread the authentication model would have to change slightly. 
1) RSS You aren't logged in to view ie no session on the server
2) Some sort of auth token would have to be passed to identify and correctly validate this user
3) These urls *choice of user here* be shared or not..

But I am totally for it if there is a plugin or something.
I agree about the email problem.
That's why I was going to use the RSS feeds and add them to Feedmailer, and let my mailserver do all the overhaul :D

---

