---
title: "Is usplash architecture dependant?"
date: 2008-12-26
forum: General Help
---

### Post by Flimm on 2008-12-26
Is usplash architecture dependant? Can I distribute one .so file to everyone or do 64 bit computers need a seperate .so file?

---

### Post by Flimm on 2009-01-03
bump

---

### Post by red_team316 on 2009-01-04
The .so file is architecture dependant.

Although, you could just provide the source in a deb package and have it build it and then install it. That way you wouldn't need to compile separate .so files for x86 x86_64.

---

### Post by Flimm on 2009-01-20
Thanks red_team316. It gets worst than that too, not only are usplash themes dependent on the architecture they're built for, they're also dependent on the version of usplash, so a usplash theme built for Intrepid won't work on Hardy. (It'll give you an usable image error) I found that one out the hard way.

---

