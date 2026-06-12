---
title: "kernel upgrade and soundcore"
date: 2006-05-28
forum: Desktop Environments
---

### Post by djpate on 2006-05-28
hello all,

I was using xubuntu with no trouble at all but i bought a DVBT card witch was not supported by my kernel so i updated my kernel to 2.6.16.18 following a tutorial on this forum.

Now my dvbt card works but i lost all sound!
after a weekend of investigation i found out that probably because soundcore is not set right.
modinfo soundcore return an error.
but i'm a total newb in kernel config and i don't know where the ** i cant enable that soundcore thing.

Please help me out i dont want to have to switch back to windows because of this.
tia

---

### Post by hw-tph on 2006-05-28
In kernel configuration, select *Device drivers --> Sound --> Sound card support* as a module (hit M if you're using menuconfig).


Håkan

---

