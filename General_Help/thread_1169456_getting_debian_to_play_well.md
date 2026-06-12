---
title: "getting debian to play well"
date: 2009-05-25
forum: General Help
---

### Post by salvachn on 2009-05-25
I installed Ubuntu 9.04 on a drive alongside XP and it worked well. I got a friend's old 40GB hard disk and installed Fedora 10 and Debian 5 on it. I still have space for Ubuntu Server which I intend to install over the weekend. I updated ubuntu's grub by copying Debian's grub entries. Fedora worked well since it has root=uuid=<disk_label_or_whatever>, but Debian doesn't have and so I can't boot into Debian from Ubuntu. I need to find the disk label for the debian partition. Please help me:)

---

### Post by salvachn on 2009-05-25
OK. I found out by trial and error. The command is

```
#blkid.
```

---

