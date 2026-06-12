---
title: "How would I patch grub"
date: 2009-04-19
forum: General Help
---

### Post by swoll1980 on 2009-04-19
I installed fedora 11. I can't boot into it though because I my old grub wont boot ext4. I don't want to mess with my Ubuntu install so I left the grub alone. I found a patch [here]("mail-archive.com/bug-grub@gnu.org/msg11458.html") to add ext4 support to grub. How would I add it.

---

### Post by Polygon on 2009-04-19
i would talk to the fedora guys about this, since ubuntu had to patch their version of grub to make it work

anyway, it usually involves downloading the grub source, then running the cli program 'patch' against the grub source

man patch and see if you can figure it out

---

### Post by swoll1980 on 2009-04-19
Sounds complicating Maybe I should just download jaunty, and install the grub from that one

---

### Post by Skripka on 2009-04-19
> **swoll1980 said:**
> Sounds complicating Maybe I should just download jaunty, and install the grub from that one

Or grab a SuperGRUB disk.

---

