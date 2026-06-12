---
title: "64-Bit and Gaming - Cedega"
date: 2006-04-14
forum: Gaming &amp; Leisure
---

### Post by johnnymac on 2006-04-14
Just a quesiton - I've been gaming with 32-bit but does cedega have plans or can you run it via 64-bit environment.  I don't want to chroot it either.

---

### Post by bonzodog on 2006-04-14
not exactly, as the games you would be running would be 32 bit, so it needs to retain the 32 bit API. What they suggest is running cedega using the ia32-lib connections, and linux 32, which makes the app run as if it was in a 32 bit env. I'm not sure how you achieve this though.

---

### Post by Kemotaha on 2006-04-14
It is easy.  you install the ia32 libs package which might be already installed.  Then you install cedega-small with dpkg -i --force-architecture.  Sometimes you have to add /lib32 and /usr/lib32 to the file but I haven't had to do that since cedega 5 came out.

---

