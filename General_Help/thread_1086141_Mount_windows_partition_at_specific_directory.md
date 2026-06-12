---
title: "Mount windows partition at specific directory"
date: 2009-03-03
forum: General Help
---

### Post by jb64 on 2009-03-03
Hi.  I would like to mount my windows partition, but I would not like the entire partition to be accessible - I only want C:\Users\Jason to be accessible.  Obviously NTFS doesn't support Unix permissions, so that's out of the question.  

Any thoughts?

---

### Post by dcstar on 2009-03-03
> **jb64 said:**
> Hi.  I would like to mount my windows partition, but I would not like the entire partition to be accessible - I only want C:\Users\Jason to be accessible.  Obviously NTFS doesn't support Unix permissions, so that's out of the question.  

Any thoughts?

You can probably mount it with the "user" option and then do a Share on that directory.

---

### Post by bodhi.zazen on 2009-03-03
You will have to mount the entire windows partiton (you can not mount just a single directory from our C:\ )

In addition, since NTFS does not support permissions you will have the same ownership and permissions for all directories and files on the partition.

You are probably best off making a data partition.

---

