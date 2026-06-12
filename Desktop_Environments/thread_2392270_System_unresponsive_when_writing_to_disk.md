---
title: "System unresponsive when writing to disk"
date: 2018-05-18
forum: Desktop Environments
---

### Post by tigrezno on 2018-05-18
This has happened to me for the last 2-3 versions of Ubuntu. No matter what, I always get an unresponsive system when an app is writing to disk.

I've used smarctl to check my SSD and it shows nothing wrong, no tests failed, no failed stats, nothing. I really hate it and I've been thinking of switching distributions to see if it's an ubuntu thing.

I don't know what to do.

---

### Post by mörgæs on 2018-05-19
Yes, it's a good initial test. It will tell if it's a software or hardware problem.

---

### Post by tigrezno on 2018-05-19
Just discovered my SSD was using CFQ scheduler for some odd reason. I expect my problem to go away since changing it to Deadline.

---

### Post by mörgæs on 2018-05-19
Good, please mark the thread solved if it works.

---

