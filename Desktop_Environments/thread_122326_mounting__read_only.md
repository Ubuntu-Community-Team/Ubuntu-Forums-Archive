---
title: "mounting / read only"
date: 2006-01-27
forum: Desktop Environments
---

### Post by aias on 2006-01-27
Hi,

I am using JFS with the stock ubuntu kernel.  I want to mount / and /usr (two separate partitions) read-only for security.   However, I noticed that init displays a message during booting that says "creating device nodes".  My question is, if I setup / to be read-only, will I get a kernel panic when it tries to create the nodes or is this happening in memory before it pivot roots it to disk?  

Thanks
ajay

---

### Post by Hairy_Palms on 2006-01-27
/ and /usr are read only for users by default, only root can access them, if you set them both as unreadable by root then you could never change any files which would be a bit pointless.

---

