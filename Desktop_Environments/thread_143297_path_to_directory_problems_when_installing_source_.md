---
title: "path to directory problems when installing source packages"
date: 2006-03-12
forum: Desktop Environments
---

### Post by lex1 on 2006-03-12
It seems every time I install a source package or tar it does not registerer at prompt
and I must go to .bashrc and bash-profile and add the line export PATH=/usr/local/ssl/bin:$PATH in the case of ssl or openssl

what I want to know is if future when I install a programme package or tar ball
from source what must I do in the fist instance so it will appear at the command prompt.

lex1;) ;)

---

### Post by taurus on 2006-03-12
It depends where you want to install it.  You can declare the destination directories during the ./configure part!
```

./configure --PREFIX=/usr/local

```
However, most of the time, the program will try to install the binary in /usr/local/bin, libraries in /usr/local/lib, share in /usr/local/share, etc.  But if you decide to install it somewhere else, then you need to either create a symbolic link to the binary or include it in your path!!!

---

