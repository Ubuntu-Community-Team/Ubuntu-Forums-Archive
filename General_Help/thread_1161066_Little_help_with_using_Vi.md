---
title: "Little help with using Vi"
date: 2009-05-16
forum: General Help
---

### Post by pro003 on 2009-05-16
I was wandering is there a command to cut off / remove / delete  long lines in text, for example delete all lines longer than 80 characters?

I would really appreciate any help.

thnx

---

### Post by zacktu on 2009-05-16
*z*

---

### Post by wanchai on 2009-05-16
Interesting question. I suppose, regular expressions will be part of the solution.

For example:```

%g/^.\{80\}/d
```
will delete all lines with at least 80 characters.

For truncation you might want to read Section 4.5 in [http://www.geocities.com/volontir/#substitute](http://www.geocities.com/volontir/#substitute) You could probably use a regular expression with two parts, one that matches the first n characters and one that matches the rest. With \2 you can replace the second match with nothing.

---

### Post by pro003 on 2009-05-16
wanchai, I could by you a beer for this, you have no idea how much you helped me with this!

thanks 1000x

---

### Post by pro003 on 2009-05-19
wanchai, I don't wanna push you, but could you also know how could I remove lines containing less then x number of characters? 

thnx

---

