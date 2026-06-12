---
title: "Hard Drive Upgrade Information"
date: 2009-05-02
forum: General Help
---

### Post by KegHead on 2009-05-02
Hi!

I'd like to update my hard drive. Is there a software package to image my current setting and transfer it to my new drive?

I'm new to Ubuntu and looking for an easy solution.

Thanks in advance.

KegHead.

---

### Post by todak on 2009-05-02
[Clonezilla]("http://clonezilla.org/") is the easiest, IMO.

---

### Post by dcstar on 2009-05-02
> **KegHead said:**
> Hi!

I'd like to update my hard drive. Is there a software package to image my current setting and transfer it to my new drive?

I'm new to Ubuntu and looking for an easy solution.

Thanks in advance.

KegHead.

This will copy your current data to a new drive byte for byte (substitute the correct names etc):

```
dd if=/dev/old-drive of=/dev/new-drive
```

---

### Post by KegHead on 2009-05-03
Hi!

Thank you for the quick reply!

KegHead

---

