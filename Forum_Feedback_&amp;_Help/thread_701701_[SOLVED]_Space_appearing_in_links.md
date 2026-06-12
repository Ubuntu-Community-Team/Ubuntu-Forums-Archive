---
title: "[SOLVED] Space appearing in links"
date: 2008-02-19
forum: Forum Feedback &amp; Help
---

### Post by Cappy on 2008-02-19
Can anyone shed some light on why this ends up with spaces:

mirrors.kernel.org/debian/pool/main/libs/libssh2/libssh2-1_0.18-1_i386.deb
mirrors.kernel.org/debian/pool/main/o/openldap2.3/libldap-2.4-2_2.4.7-4_i386.deb

I can't use a url tag on them because they are arguments for getlibs. If they were a url link they wouldn't be able to be copy and pasted because they would be shortened.

Eg.

> 
sudo getlibs -w mirrors.kernel.org/debian/pool/main/libs/libssh2/l ibssh2-1_0.18-1_i386.deb
sudo getlibs -w mirrors.kernel.org/debian/pool/main/o/openldap2.3/ libldap-2.4-2_2.4.7-4_i386.deb


---

### Post by Cappy on 2008-02-29
There is a 50 character limit per word.

Using code tags gets around this. It's blatantly obvious now. Marked as solved.

---

