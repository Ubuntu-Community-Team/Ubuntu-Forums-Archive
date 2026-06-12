---
title: "How does WUBI work???"
date: 2009-10-25
forum: Desktop Environments
---

### Post by Barriehie on 2009-10-25
Hello all,
I'll be giving a friend of mine the 8.04 LTS LiveCD to check out and I noticed it has a wubi something on there.  Will this allow him to repartition his drive and setup a dual boot via grub?  I didn't use wubi when I installed ubuntu; I just blew away XP!!!

Barrie

---

### Post by ST3ALTHPSYCH0 on 2009-10-26
Wubi is installed within windows, and it creates a folder that contains its partition. You can choose whatever drive and partition size you like,and it will use the windows boot loader instead of grub. It's nice for a "getting to know you" phase (I have 9.10 installed as wubi), but when I was playing with 9.04 I found that it has some instability that way. The nice thing is, if your friend doesn't like it, it can be uninstalled through add/remove programs. The bad thing is that it's not designed to be a permanent install.

---

### Post by Barriehie on 2009-10-26
> **ST3ALTHPSYCH0 said:**
> Wubi is installed within windows, and it creates a folder that contains its partition. You can choose whatever drive and partition size you like,and it will use the windows boot loader instead of grub. It's nice for a "getting to know you" phase (I have 9.10 installed as wubi), but when I was playing with 9.04 I found that it has some instability that way. The nice thing is, if your friend doesn't like it, it can be uninstalled through add/remove programs. The bad thing is that it's not designed to be a permanent install.

Thank you, that's just the answer I was needing!

Barrie

---

### Post by ST3ALTHPSYCH0 on 2009-10-27
N/p.

---

