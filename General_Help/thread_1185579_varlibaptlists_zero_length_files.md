---
title: "/var/lib/apt/lists zero length files"
date: 2009-06-12
forum: General Help
---

### Post by imbjr on 2009-06-12
Just had a power-cut and after bootup I decided to check that I hadn't gotten some zero-length files created due to ext4.

Some data files on a project I'm working on did get zeroed, but I also uncovered zero-length files in /var/lib/apt/lists - with time stamps pointing to about 2am this morning, which is odd (wasn't switched on then!). 

For example, security.ubuntu.com_ubuntu_dists_jaunty-security_restricted_bimary-i386_Packages iz zero length, but so are source-related files which kinda makes sense since I have not had cause to access source code - as far as I'm aware.

Are they supposed to zero-length tho?

---

### Post by michy99 on 2009-06-12
If you have any doubts, a sudo apt-get update should fix them up.

---

### Post by imbjr on 2009-06-12
Yup, did that and nothing seemed to update.

Fingers-crossed, it'll be ok - must just have to keep an eye out for a lack of updates.

---

