---
title: "Cannot get new HDD to work"
date: 2009-02-08
forum: General Help
---

### Post by rugbert on 2009-02-08
I just opened my server and found, hey theres an unused hard drive in there! but plugging in it gave me some super block errors, I corrected it (actually I didnt, I tried running e2fsck but it kept saying it was mounted when it really wasnt. Then I rebooted and everything seemed fine) and then tried to mount it. But it wouldnt go

running fdisk gave me an error
```

disk /dev/sde doesn't contain a valid partion table

```

so I ran mkfs -V -t ext3 /dev/sde but I still get that partition error. I think I've forgotten how to make partitions, but I thought mkfs did it automatically.... Am I forgetting something or is the HDD dead?

---

### Post by cariboo on 2009-02-08
You have to create a partition before you can make the file system. Actually I have created a file system with out partitioning the disk, but it kept erroring out.

See as this is a server at the prompt type:

```
sudo fdisk /dev/sde
```

and create a partition. For help in fdisk press m

Jim

---

