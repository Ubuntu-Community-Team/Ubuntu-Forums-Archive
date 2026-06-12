---
title: "When does fstab mount volumes?"
date: 2010-03-15
forum: Desktop Environments
---

### Post by NiGhtMarEs0nWax on 2010-03-15
Is it after a user logs in or as soon as the system boots?

I suspect as soon as the system boots due to it being located in the etc directory, just need this clarified.


Thanks.

---

### Post by mcduck on 2010-03-15
Pretty much immediately after the kernel is loaded into RAM when the system is booting.

It would be quite hard to access any files from your hard drive and start all the services if the root partition wasn't mounted at that point.. ;)

---

### Post by NiGhtMarEs0nWax on 2010-03-15
very true. :P

Thanks.

---

