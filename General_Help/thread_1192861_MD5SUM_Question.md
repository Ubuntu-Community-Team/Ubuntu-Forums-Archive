---
title: "MD5SUM Question"
date: 2009-06-20
forum: General Help
---

### Post by Psycho.mario on 2009-06-20
If i have a file called test.txt and i get the hash, is it possible to recreate the file test.txt from the hash?

This may sound like a stupid question to some people but i am new to hashes

Thanks in advance

---

### Post by geirha on 2009-06-20
No, it's only a fingerprint of a file; it's not a type of compression. It's one of the reasons why the passwords in /etc/shadow are stored as the md5sum of the password, rather than the password itself. If you only have the md5sum, the only way to find the password is by brute force; do the md5sum of every conceivable password until you find one that produces the same md5sum.

---

