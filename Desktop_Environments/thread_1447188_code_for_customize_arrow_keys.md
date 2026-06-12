---
title: "code for customize arrow keys"
date: 2010-04-05
forum: Desktop Environments
---

### Post by sasnfbi1234 on 2010-04-05
that is a : (   (no space but it auto made it a :()

---

### Post by loell on 2010-04-05
just title your thread as "custom key codes for arrow directions".  :)

ok, i'll probably do it for you.

do, repost your code.

---

### Post by sasnfbi1234 on 2010-04-05
```
c=12322123;x=85;y=20;while read -sn1 p;do k=${c:(p-1)*2:2};let x+=$((k/10-2));let y+=$((k%10-2));echo -en \\033[$y\;"$x"HX;done

```

---

### Post by loell on 2010-04-05
ok this is already a duplicate thread, since you already have an existing thread in programming talk category, pls.  continue with that thread. 

thread close.

---

