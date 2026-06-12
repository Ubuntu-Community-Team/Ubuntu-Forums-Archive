---
title: "[SOLVED] spss files with other tools?"
date: 2007-12-03
forum: Education &amp; Science
---

### Post by Scarath on 2007-12-03
Is there anyway of converting Spss files to open in another (open source) tool?

Preferably 'R', Salstat or PSPP?

thanks

---

### Post by UbuWu on 2007-12-04
I think rkward can import spss files, but I am not sure...

---

### Post by akniss on 2007-12-05
> **Scarath said:**
> Is there anyway of converting Spss files to open in another (open source) tool?
Preferably 'R', Salstat or PSPP?
thanks

I've never actually used it (as I'm not an SPSS user) so I can't speak to its usefulness, but R has a function to read in spss files.
```
R
library(foreign)
?read.spss
```

---

### Post by Scarath on 2007-12-06
thanks guys

---

