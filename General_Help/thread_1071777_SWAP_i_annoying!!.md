---
title: "SWAP i annoying!!"
date: 2009-02-16
forum: General Help
---

### Post by alex1996arm on 2009-02-16
Let me explain my situation.I have just achieved a quad boot.
opensolaris has the control of the mbr.
i boot ubuntu and it detects it as swap and writes over it,so how could i disable swap permanently in ubuntu?

---

### Post by kerry_s on 2009-02-16
gksu gedit /etc/fstab

# out the swap line

---

### Post by alex1996arm on 2009-02-16
Thanks!
:KS

---

