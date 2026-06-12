---
title: "dmesg setkeycodes error"
date: 2005-10-17
forum: Desktop Environments
---

### Post by department27 on 2005-10-17
Hi,

I keep getting this in dmesg:

[4307082.440000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4307082.566000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).

I'm running breezy on a dell d600 which a port replicator and a kwm, so the lid is shut.

Any help with the error would be great or even how do I stop it.

---

### Post by Xen2oo6 on 2005-10-17
I get the error message, too!

---

### Post by chunk on 2005-10-17
me three

---

### Post by linuxworld on 2005-10-17
yup same here

dmesg output 
[4296333.293000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296333.439000] atkbd.c: Unknown key released (translated set 2, code 0xaa on i sa0060/serio0).

found it on bugzilla [http://bugzilla.ubuntu.com/show_bug.cgi?id=17807](http://bugzilla.ubuntu.com/show_bug.cgi?id=17807)

---

