---
title: "[SOLVED] Incorrect HDD recognition"
date: 2008-12-14
forum: General Help
---

### Post by azathrael on 2008-12-14
When I go to File System, right click, properties, and look at Free Space, it only says ~800 MB, or the latest bunch of files I deleted.  But when I go to Partitions Editor and look at my HDD, it says I have over 7 GB left.  How is there a discrepancy between Free Space that's actually there and what my File System says?

I think this has a relevance to my other problem, which was getting when SCIM-bridge and SCIM-launcher kept crashing all my applications and taking up 100% CPU.

PS: I also unmounted my 2nd HDD in this laptop that had Vista and formated to ext3 using the Partitions Editor.  But when I try to transfer files to that HDD, it gives me an error saying that I don't have authorization from the HDD.  How do I access the HDD?

Thanks.

---

### Post by logos34 on 2008-12-14
> **azathrael said:**
> 
PS: I also unmounted my 2nd HDD in this laptop that had Vista and formated to ext3 using the Partitions Editor.  But when I try to transfer files to that HDD, it gives me an error saying that I don't have authorization from the HDD.  How do I access the HDD?

you need to chown and chmod it:

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
(bottom)

---

### Post by azathrael on 2008-12-15
Thank you so much!

---

### Post by logos34 on 2008-12-15
sure thing! Go to >Thread Tools>Mark as solved.  Enjoy

---

