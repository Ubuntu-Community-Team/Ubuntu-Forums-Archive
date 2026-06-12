---
title: "I can't find things"
date: 2006-10-30
forum: Desktop Environments
---

### Post by frankelr on 2006-10-30
As a recent arrival from dare I say it "windows", I'm trying to find equivalent functionality to windows explorer. Probably I just don't know how to use it, but I'd like to know how much space remains in my ext3 partition and while I'm asking, I'd like to know 
how to access another ext3 parttion left over from an earlier install.  Yes, Ubuntu shows that partition as hda2 snd it contains something called "lost and found"

---

### Post by RoyArne on 2006-10-30
The df command reports file system disk space usage. Just

```
df
```

shows the space remaining on all currently mounted file systems. Try

```
man df
```

for more information.

---

