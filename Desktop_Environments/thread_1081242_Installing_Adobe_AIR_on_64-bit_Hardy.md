---
title: "Installing Adobe AIR on 64-bit Hardy"
date: 2009-02-26
forum: Desktop Environments
---

### Post by lduperval on 2009-02-26
Hi,

I am trying to install Adobe AIR on my Hardy (64bit) machine but I cannot get it to work.

I followed the instructions on Adobe's site, but when I try to run the installer I get:

Error loading the runtime (libnss3.so: wrong ELF class: ELFCLASS64)

Also, on a related note, after following Adobe's instructions, I could no longer launch OpenOffice3 (installed from Sun's site). So I had to re-install the libnss and libnspr4 packages to make everything work again.

Error loading the runtime (libnss3.so: wrong ELF class: ELFCLASS64)

Thanks,

L

---

### Post by aniket ray on 2009-03-05
You need the 32-bit version of libnss library.
You can find more details here: [http://kb.adobe.com/selfservice/viewContent.do?externalId=kb408084](http://kb.adobe.com/selfservice/viewContent.do?externalId=kb408084)

---

