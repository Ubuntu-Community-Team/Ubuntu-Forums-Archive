---
title: "How Do I Figure Out What Graphics Card I Have?"
date: 2009-06-24
forum: General Help
---

### Post by Ubuntist on 2009-06-24
I've just installed Jaunty on a hand-me-down Compaq nc4400 laptop.  How can I figure out what graphics card it has?

---

### Post by jocko on 2009-06-24
> **Ubuntist said:**
> I've just installed Jaunty on a hand-me-down Compaq nc4400 laptop.  How can I figure out what graphics card it has?
You could type:
```
lspci | grep VGA
```in a terminal. I'm guessing you'll find it's got an Intel gma 950 (that's what google tells me).

---

### Post by Ubuntist on 2009-06-24
Thanks!  And you're very close: it's a 945GM....

So now I now that nothing regarding ATi or nVidia applies to me.

---

