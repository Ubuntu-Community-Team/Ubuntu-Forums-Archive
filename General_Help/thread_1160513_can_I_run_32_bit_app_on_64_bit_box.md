---
title: "can I run 32 bit app on 64 bit box?"
date: 2009-05-15
forum: General Help
---

### Post by firsttimeuser on 2009-05-15
the application was compiled on a 32 bit ubuntu and is it possible that I can run it on a 64bit ubuntu?

thanks!

---

### Post by Joeb454 on 2009-05-15
What application is it, chances are there will be a 64 bit version available (especially if you installed it through the repo's).

I think you *can* run it, but it would be easier (and preferable) to use the 64 bit version

---

### Post by firsttimeuser on 2009-05-15
it gives me this no such file or directory error

root@:/tmp# file tac_plus
tac_plus: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.6.15, dynamically linked (uses shared libs), not stripped
root@:/tmp# ldd tac_plus
        not a dynamic executable


root@:/tmp# ./tac_plus
bash: ./tac_plus: No such file or directory

---

