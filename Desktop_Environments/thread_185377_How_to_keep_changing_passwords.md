---
title: "How to keep changing passwords?"
date: 2006-05-31
forum: Desktop Environments
---

### Post by jsmidt on 2006-05-31
Let's say I wanted Ubuntu to force/prompt me to change my password every six mounts. How would I go about doing that?

---

### Post by jazzmuzik on 2006-05-31
Run this for some info on the chage command:

```
man chage
```

Here's more:

[http://tinyurl.com/mqhdw](http://tinyurl.com/mqhdw)

---

### Post by 5-HT on 2006-05-31
You could easily set an account password to expire after a defined period of time  if that would be acceptable. Descriptions the relevant options are documented in passwd's man page.

I don't know of any utility off-hand that would use the number of mounts as the criterion. However, you may be able to write a little script to keep track mounts and have passwd expire the password immediately (see the man page) after the target number is reached (not really sure of this though, but it may provide a starting point).

HTH

---

