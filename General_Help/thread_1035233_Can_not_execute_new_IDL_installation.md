---
title: "Can not execute new IDL installation"
date: 2009-01-09
forum: General Help
---

### Post by levyg on 2009-01-09
Hi Folks, 
 I am new to ubuntu and I have installed IDL 7.0 under /usr/local/itt/idl70. When I run idl it tells me that he can not execute the file /usr/local/itt/idl70/bin/bin.linux.x86/idl, however the file it exists and have permissions to be executed. I did try to execute it my self but it does not responds. 
Does anyone knows what it is happening?

Thanks,

Giorgio

---

### Post by drdenim on 2009-01-09
I'm not really sure what is causing the problem, but have a working copy of IDL 7.0 on ubuntu if you need to compare anything.

See what ubuntu thinks the file is with the 'file' command (file /usr/local/itt/idl70/bin/bin.lunux.x86/idl)

I get:
```

idl: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.2.5, dynamically linked (uses shared libs), not stripped

```

Yours could be different, not entirely sure.  But maybe it will reveal something.

---

