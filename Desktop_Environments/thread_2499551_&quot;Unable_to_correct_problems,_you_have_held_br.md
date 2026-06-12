---
title: "&quot;Unable to correct problems, you have held broken packages&quot;"
date: 2024-07-31
forum: Desktop Environments
---

### Post by blort on 2024-07-31
I'm trying to install wine32 on ubuntu 222.04.

When I do "apt-get install wine32", I get:

```
The following packages have unmet dependencies:
 libgphoto2-6:i386 : Depends: libgd3:i386 (>= 2.1.0~alpha~) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```


How do I fix this and install wine32?

---

### Post by guiverc on 2024-07-31
I see the package available for Ubuntu 22.04 LTS

```

 libgd3 | 2.3.0-2ubuntu2          | jammy           | amd64, arm64, armhf, i386, ppc64el, riscv64, s390x

```

but the "*you have held broken packages*" maybe the result of prior command errors, OR other incorrect decision made earlier (ie. you've not said what *architecture* you're using).

Running `sudo apt install -f` may help, or at least let you get more issues on your problem.

---

