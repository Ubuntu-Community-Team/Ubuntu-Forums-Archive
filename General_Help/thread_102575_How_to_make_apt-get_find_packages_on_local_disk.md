---
title: "How to make apt-get find packages on local disk?"
date: 2005-12-12
forum: General Help
---

### Post by Kronocide on 2005-12-12
Hi,

I see that all the example lines in /etc/apt/sources.list are HTTP URLs. How can I add a directory on my local disk, where I have copies package files? I don't have a network card on this box, that's why I have to do it this way.

Any help appreciated.

---

### Post by stuporglue on 2005-12-12
Try copying the file(s) into /var/cache/apt/archives/ then run the install command again. I think it will pick them up there.

---

### Post by Ufo on 2005-12-13
There is also how-to for adding personal repositories in wiki:

[https://wiki.ubuntu.com/PersonalRepositories?highlight=%28repository%29](https://wiki.ubuntu.com/PersonalRepositories?highlight=%28repository%29)

---

