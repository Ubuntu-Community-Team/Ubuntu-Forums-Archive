---
title: "Thunderbid stopped working as a news feeder"
date: 2006-08-11
forum: Desktop Environments
---

### Post by foxy123 on 2006-08-11
Has anyone else experienced this? It started some time ago, maybe a week or two, TB stopped to update news feeds. Today I decided to remove the existing News & Blogs account and re-add the feeds. Everything stops on 
```
Verifying RSS feed...
```

Why?

---

### Post by foxy123 on 2006-08-12
I've found the following in the Java Script Console, after I opened TB and tried to add a feed:
```
Error: [Exception... "Component returned failure code: 0x80570015 (NS_ERROR_XPC_CI_RETURNED_FAILURE) [nsIJSCID.createInstance]"  nsresult: "0x80570015 (NS_ERROR_XPC_CI_RETURNED_FAILURE)"  location: "JS frame :: chrome://messenger-newsblog/content/feed-parser.js :: <TOP_LEVEL> :: line 41"  data: no]
Source File: chrome://messenger-newsblog/content/feed-parser.js
Line: 41
```

```
Error: uncaught exception: [Exception... "Component returned failure code: 0x80570015 (NS_ERROR_XPC_CI_RETURNED_FAILURE) [nsIJSCID.createInstance]"  nsresult: "0x80570015 (NS_ERROR_XPC_CI_RETURNED_FAILURE)"  location: "JS frame :: chrome://messenger-newsblog/content/feed-parser.js :: <TOP_LEVEL> :: line 41"  data: no]
```

```
Error: uncaught exception: [Exception... "Component returned failure code: 0x80570015 (NS_ERROR_XPC_CI_RETURNED_FAILURE) [nsIJSCID.createInstance]"  nsresult: "0x80570015 (NS_ERROR_XPC_CI_RETURNED_FAILURE)"  location: "JS frame :: chrome://messenger-newsblog/content/Feed.js :: anonymous :: line 123"  data: no]
```

I have no idea what it means though...

---

### Post by wilberfan on 2006-08-15
I just installed Thunderbird, and imported my two dozen RSS subscriptions from my Windows box....   NONE of my RSS feeds are getting updated.  :-(

It sounds like this has worked in the past--but now doesn't??   I LOVE Thunderbird (and my blogs); I'd hate to have to give it up...

---

### Post by foxy123 on 2006-08-15
I had to remove the old profile and create a new one to make it work again...

---

### Post by wilberfan on 2006-08-16
> **foxy123 said:**
> I had to remove the old profile and create a new one to make it work again...

I tried that, and it worked--but only for a short time.   My feeds are again not updating.  It looks like it's trying--that "activity bar" at the bottom keeps scanning back and forth for a long time, but I'm not getting any results...   (The 'throbber' spins endlessly, too.)

Any ideas?

---

### Post by wilberfan on 2006-08-16
We may have hit a bug in Thunderbird:  [https://bugzilla.mozilla.org/show_bug.cgi?id=322793](https://bugzilla.mozilla.org/show_bug.cgi?id=322793)

:-(

---

### Post by wilberfan on 2006-08-16
Some additional info:

In my case, it seems that the RSS feeds work--until I sort them into different folders?  

Don't know why that would create a problem...

S.

---

### Post by foxy123 on 2006-09-14
I hit it again and yes, it's definitely a bug posted above.

Thanks to wilberfan's link I found a solution. It is described [here]("http://forums.mozillazine.org/viewtopic.php?t=384960&start=15&postdays=0&postorder=asc&highlight=")

Although there a couple of solution, just removing 'feeditems.rdf' worked fine for me.

---

