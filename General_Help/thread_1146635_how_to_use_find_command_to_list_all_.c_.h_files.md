---
title: "how to use find command to list all .c .h files?"
date: 2009-05-02
forum: General Help
---

### Post by yinglcs2 on 2009-05-02
Hi, 

how to use find command to list all .c .h files?

I tried 
find . -name '*.[cpp|h]' 
find . -name '*.cpp' -name '*.h'

both did not work.

Thank you for any help.

---

### Post by chili555 on 2009-05-02
After doing:```
sudo updatedb
```This will take a few moments; please be patient. Now do:```
locate *.c | less
```I added *| less* because there are quite a stack of them.

---

### Post by kaibob on 2009-05-02
The following should work:

```
find . -name '*.cpp' -o -name '*.h'
```

---

### Post by Jose Catre-Vandis on 2009-05-02
```
find -name '*.c' -or -name '*.h'
```

But they will need sorting :)

You could however use
```
 find -name '*.c' & find -name '*.h'
```
to get separate lists, sorted by extension

---

