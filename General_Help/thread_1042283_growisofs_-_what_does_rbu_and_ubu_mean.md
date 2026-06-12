---
title: "growisofs - what does rbu and ubu mean?"
date: 2009-01-17
forum: General Help
---

### Post by miatawnt2b on 2009-01-17
I am just curious about the output of growisofs.  What does RBU and UBU mean?

Thanks,
-J

---

### Post by kruykaze on 2009-04-15
I'd like to know too.

---

### Post by robbak on 2009-05-06
The Acronyms are "Ring Buffer Utilisation" and "Unit Buffer Utilisation"

The "Ring Buffer" is a memory buffer created and maintained by growisofs' builtin dd. It is 32 MB by default, according to the code I was just reading - if that is still the case, it might be time to increase that! - there has to be a config somewhere, but I am getting off track.
The "Unit Buffer" is the buffer inside the DVD drive. By appearances, growisofs tries to keep it at around 60%

---

