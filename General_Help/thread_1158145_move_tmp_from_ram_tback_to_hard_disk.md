---
title: "move tmp from ram tback to hard disk"
date: 2009-05-13
forum: General Help
---

### Post by Shady3D on 2009-05-13
i've changed the mount point of the /tmp to the ram and it turned bad on me, the PC became very slow one using more application, so i want to revers it.

i moved the /tmp dirctory to the ram by adding this line at the end of **etc/fstab**
```

none /tmp tmpfs nr_inodes=200k,mode=01777,nosuid,nodev 0 0

```

so i tried to be smart and just removed the line, but i can't enter the session, just use the Terminal in CTRL+ALT+F1 to login

if anybody knows how to reverse that curse, it will that be great

---

### Post by Wtwine on 2013-03-18
I am exactly in the same boat, four years later. 
Anybody have an answer to this?

Thanks

---

### Post by varunendra on 2013-03-18
> **Wtwine said:**
> I am exactly in the same boat, **four years later. **
Anybody have an answer to this?

Thanks

Things change very fast in cyber world, better start your own thread.
Feel free to link this one as reference if you wish.

This one is ... Closed.

---

