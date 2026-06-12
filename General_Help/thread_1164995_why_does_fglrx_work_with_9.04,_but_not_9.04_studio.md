---
title: "why does fglrx work with 9.04, but not 9.04 studio?"
date: 2009-05-20
forum: General Help
---

### Post by Mzwo on 2009-05-20
hi,

title says it all really. fglrx (mobility Radeon HD 2400) works absolutely fine with regular 9.04 64 bit, but 9.04 studio (also 64 bit) crashes on start up. why?

cheers,
Mzwo

---

### Post by CatKiller on 2009-05-20
I'd imagine that it's because Ubuntu Studio uses a different kernel. If the driver were open source, it could be compiled against any kernel without the need for binary blobs that may or may not work. As it is, they'll compile their drivers for a particular kernel and then have to re-compile them and re-release them whenever a new kernel comes out. Or not bother, and leave those users out in the cold. Or, at least, that's how the NVidia drivers work.

---

### Post by Mzwo on 2009-05-26
i see. sounds reasonable, i suppose. 

i'm not bothered, really, studio works fine with the open source driver. 

thanks,
Mzwo

---

