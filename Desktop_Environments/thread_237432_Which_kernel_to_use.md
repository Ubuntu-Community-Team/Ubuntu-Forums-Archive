---
title: "Which kernel to use?"
date: 2006-08-16
forum: Desktop Environments
---

### Post by atomSmith on 2006-08-16
I just got an IBM Intellistation Z Pro (6221) with 2 XEONs and 8GB (!) RAM, and I installed Ubuntu Desktop, but running "top" shows only 1 processor, and 3.62 GB ram.

I expected the 1 processor thing, since I guessed an SMP kernel wouldn't be the default, but the RAM weirdness threw me.

Does anyone know which kernel I can install to take care of both these issues in one go?

(also, I ran the full MemTest86 3.2 without errors so I know the ram is good)

Thanks!

---

### Post by az on 2006-08-16
> **atomSmith said:**
> I just got an IBM Intellistation Z Pro (6221) with 2 XEONs and 8GB (!) RAM, and I installed Ubuntu Desktop, but running "top" shows only 1 processor, and 3.62 GB ram.

I expected the 1 processor thing, since I guessed an SMP kernel wouldn't be the default, but the RAM weirdness threw me.

Does anyone know which kernel I can install to take care of both these issues in one go?

(also, I ran the full MemTest86 3.2 without errors so I know the ram is good)

Thanks!

sudo apt-get install linux-686

Ther eis a limit to four gigs of ram with the 386 kernel.  386 is the default kernel for the desktop on all machines  -  you need to install a different kernel yourself.

---

