---
title: "Lost files while transferring to ext3 partition"
date: 2008-12-18
forum: General Help
---

### Post by je1117 on 2008-12-18
Hello , hopefully someone has encountered this before...

I wanted to unrar a large archived iso over a network onto my friends computer. For one reason or another he was using XP and had installed ext2fs so he could read/write to his ext3 partition from within windows.

So I extracted the iso over the network to his ext3 partition while in windows.

Well the file never transferred to his machine and I watched as my hard drive got smaller and smaller as the file extracted. But NOW I can't find the iso that seems to be on MY computer! I tried doing all types of searches for it, and when I total up all the files in my hard drive, it's missing ~6gb (the size of the iso).

Any help with this could maintain my sanity.

---

### Post by prshah on 2008-12-18
> **je1117 said:**
> 
So I extracted the iso over the network to his ext3 partition while in windows. Well the file never transferred to his machine and I watched as my hard drive got smaller and smaller as the file extracted. 

what is the size of your /tmp?

```
sudo du -sh /tmp
```

---

