---
title: "crontab and daily ubuntu upgrade"
date: 2006-09-26
forum: Desktop Environments
---

### Post by teumima on 2006-09-26
Could I get crontab to upgrade ubuntu daily?

How would I solve the issue of the root password?

I mean I could try

* 15 * * 0-5 apt-get upgrade 

Why wouldn't that work? password?

---

### Post by jimbren on 2006-09-26
You could do that if the entry were in root's crontab file.

You would also want to precede your command above with an update entry.  Something like
```
* 10 * * apt-get update
```

I'd be cautious about the whole thing though.  Personally, I like to take a look at what I'm upgrading before I do it, but that's just me.

---

### Post by teumima on 2006-09-26
So then to make sure it would only upgrade on condition that it won't remove anything would recquire some deeper scripting.

---

### Post by jimbren on 2006-09-27
Yes, but it is pretty rare that you would need to remove a package in order to upgrade another.  I think it is, anyway.

I just like to know what I'm upgrading before I do the upgrade, is all.

---

