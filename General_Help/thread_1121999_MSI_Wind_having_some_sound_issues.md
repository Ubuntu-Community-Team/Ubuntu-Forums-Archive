---
title: "MSI Wind having some sound issues"
date: 2009-04-10
forum: General Help
---

### Post by Tralce on 2009-04-10
So my girlfriend's laptop, a re-branded MSI Wind, is having some sporadic issues with its sound output. Seemingly randomly, her computer simply will not output sound. No errors, just no sound. I have no idea where to start. I don't even know what logs to look for trouble signs in this case. 

Any ideas?

---

### Post by Elfy on 2009-04-10
I would look first in dmesg, next time it happens open a terminal and do 

```
dmesg |tail
```

Chekc what gets shown, if there is nothing that appears to be sound related start going back further, tail defaults to 10 lines

```
dmesg |tail -20
```

would give 20 lines.

IF you need help with the output then you can post it here.

---

