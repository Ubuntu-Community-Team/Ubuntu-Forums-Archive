---
title: "negative caching"
date: 2008-12-26
forum: General Help
---

### Post by sulekha on 2008-12-26
Hi,

this is what i have read about negative caching in the book , "practical guide to Ubuntu Linux by mark sobell"

Storing the knowledge that something does not exist. A cache normally stores information about something that exists. A negative cache stores the information that something, such as a record, does not exist.

can any one give an example(s) / practical situation(s) where and why this is used ?

---

### Post by iponeverything on 2008-12-27
Squid does negative caching, it saves a lot of time with not having to go out and look for something that you already know does not exist.

---

### Post by dcstar on 2008-12-27
> **iponeverything said:**
> Squid does negative caching, it saves a lot of time with not having to go out and look for something that you already know does not exist.

As long as you are sure the "non-existence" is permanent, not just a transient issue, then you can miss out on something that actually does exist (until the cache entry expires).

---

