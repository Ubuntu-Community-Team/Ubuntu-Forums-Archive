---
title: "DVD not recognized correctly"
date: 2011-09-24
forum: Desktop Environments
---

### Post by jgpacc on 2011-09-24
My DVD drive is not recognized as a writable drive. Thinks it is a read only.  Tried using Brasero, GnomeBaker and K3b.  They will not allow the drive to be selected for out put.  K3b says: 
   No CD/DVD/BD writer found.
K3b did not find an optical writing device in your system. Thus, you will not be able to burn CDs or DVDs

I have a new install of 11.04. Pretty clean not much installed.  I wanted to get a good backup process in place.  So I was planning to use Remastersys Backup.   But I can't write to the DVD drive.

The drive does work, I installed using it. 

I read some other post with a similar problem but did not see a solution.  Anyone solved this?
Thanks

---

### Post by mc4man on 2011-09-24
If it is actually a RW drive then file a bug  - what does this show in the  *-cdrom section
```
sudo lshw -C disk
```

---

### Post by jgpacc on 2011-09-24
Ah silly me. It is not a writer.
Thanks for your time.

---

