---
title: "Google Earth doesn't start"
date: 2009-04-26
forum: General Help
---

### Post by Marcos.Rufino on 2009-04-26
I'm having problems with Google Earth since Ubuntu 8.10. I upgraded to Jaunty and the problem persists. When I launch Google Earth, it shows its splash screen, then appear for a while and suddenly disappears.

I'm using Google Earth 5.0, but the same problem occurred with the previous version too.
 
I've tried to open it from terminal, and see the bellow error message:
./googleearth-bin: relocation error: /lib/i686/cmov/libssl.so.0.9.8: symbol BIO_test_flags, version OPENSSL_0.9.8 not defined in file libcrypto.so.0.9.8 with link time reference

Does anyone know how could I solve this?

Thanks,

Marcos

---

### Post by Marcos.Rufino on 2009-05-02
Any suggestion?

---

### Post by DeMus on 2009-05-02
> **Marcos.Rufino said:**
> Any suggestion?

How did you install the program? Using sudo or without it?
Without sudo:
Open a terminal and
cd google-earth
ls -l
mv libcrypto.so.0.9.8 libcrypto.so.0.9.8_org

With sudo:
Open a terminal
cd /opt/google-earth *
ls -l
mv libcrypto.so.0.9.8 libcrypto.so.0.9.8_org

What happened is: Google added a wrong version of the libcrypto file in the Google-earth package. By renaming it, the program will look for the right version, supplied by Ubuntu. Now it should work.

*  I'm not entirely sure this is the right folder. I installed it in my home folder, but if it is not the right folder, then open nautilus in /
Use search to find the right folder.

---

### Post by Marcos.Rufino on 2009-05-02
DeMus,

Thank you very much for the tip. It did work!

Marcos

---

