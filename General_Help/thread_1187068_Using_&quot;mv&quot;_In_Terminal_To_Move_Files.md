---
title: "Using &quot;mv&quot; In Terminal To Move Files"
date: 2009-06-14
forum: General Help
---

### Post by Vision1337 on 2009-06-14
Hey all, im wanting to move a patch folder to /usr/src/ and when i use:

mv rtl8187_2.6.27.patch /usr/src/

i get:

mv: cannot move `rtl8187_2.6.27.patch' to `/usr/src/rtl8187_2.6.27.patch': Permission denied

so what do i place in front of mv to make it move it as admin?

---

### Post by cyzak on 2009-06-14
try 
sudo mv rtl8187_2.6.27.patch /usr/src/

---

### Post by Vision1337 on 2009-06-14
Worked! tysm mate :) easy fixed.

---

