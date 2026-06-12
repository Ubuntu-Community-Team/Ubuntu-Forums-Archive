---
title: "ll command"
date: 2011-01-04
forum: Desktop Environments
---

### Post by keimasi on 2011-01-04
Hi 2 all
 this command show that files that start with numbers
```

ll [0-9]*

```but can u guide me how can  i find those file does not start with numbers??
(files can started by every character except / (slash)) :KS

---

### Post by keimasi on 2011-01-04
i know this command show those files that start with alphabet :
```

 l [a-z]*

```

but how should i do 2 show every files( like those start with  " or $ or * or ... ) pls help me.

---

### Post by sisco311 on 2011-01-04
> **keimasi said:**
> Hi 2 all
 this command show that files that start with numbers
```

ll [0-9]*

```but can u guide me how can  i find those file does not start with numbers??
(files can started by every character except / (slash)) :KS

```
ls [^0-9]*
```
or
```
ls [!0-9]*
```
See: ```
man bash | less +2/"Pattern Matching"
```

> **keimasi said:**
> i know this command show those files that start with alphabet :
```

 l [a-z]*

```

but how should i do 2 show every files( like those start with  " or $ or * or ... ) pls help me.


```
ls
```
;)

---

### Post by keimasi on 2011-01-04
thanks a lot it works .  :)

---

### Post by keimasi on 2011-01-04
thanks a lot it works .  :)

---

