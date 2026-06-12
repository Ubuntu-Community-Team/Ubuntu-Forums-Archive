---
title: "why don't files show up when you search for them?"
date: 2006-07-28
forum: Desktop Environments
---

### Post by djaya2 on 2006-07-28
Why do so many files not show up when you search for them?  Even when I run Nautilus as root and tell it to search the whole filesystem, there are tons of particular files that I know exist but it won't show them when I search for them.  If it won't show files that I know exist, how can I count on it to help me find files I'm not sure about?  This is maddening.

---

### Post by aysiu on 2006-07-28
```
sudo updatedb
```

---

### Post by Anduu on 2006-07-28
> **aysiu said:**
> ```
sudo updatedb
```

That is good to know.However why isn't this done automatically?

---

### Post by aysiu on 2006-07-28
It is, but not all the time. I believe it's on a schedule... once a week or something...? That command forces the database to be updated at that very moment.

---

### Post by Anduu on 2006-07-28
I see....

As always you are a great help :KS

---

