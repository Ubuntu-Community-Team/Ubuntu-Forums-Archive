---
title: "Dual boot help"
date: 2009-05-11
forum: General Help
---

### Post by spetsacdc on 2009-05-11
Hi, I'm trying to dual boot windows and linux. I have the following partitions:

1. Ubuntu
2. Large NTFS for sharing files between ubuntu and XP
3. windows xp
4. linux swap

I added this to my grub menu.lst file:

title Windows XP
root (hd0,2)
makeactive
chainloader +1

When I try to boot to windows I get ntldr is missing.

---

