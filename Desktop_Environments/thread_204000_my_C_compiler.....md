---
title: "my C compiler...."
date: 2006-06-26
forum: Desktop Environments
---

### Post by cwncool on 2006-06-26
I have gcc and cpp on my computer, but whenever I try to install something, in this case Xine, i get to the "./configure" part of the installation and it says it cannot find a suitable C compiler with this error...
```

error: no acceptable C compiler found in $PATH
See `config.log' for more details.

```
why doesn't the program reconise the C compiler? Thanx!

---

### Post by AndersAA on 2006-06-26
apt-get install build-essential(s) should solve it.

---

### Post by cwncool on 2006-06-26
that worked for the compiler, but now I get the error...
```

configure: error: zlib needed

```
what is the apt-get for zlib? Thanx!
EDIT: N/M. I got it. Thanx Anders!

---

