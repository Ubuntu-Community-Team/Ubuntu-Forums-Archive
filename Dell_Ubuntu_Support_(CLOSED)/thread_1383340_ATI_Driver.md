---
title: "ATI Driver"
date: 2010-01-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by anup807 on 2010-01-17
I have downloaded driver for my ati radeon HD 4570 from Ati.com. I downloaded a file with .run extension. when i double click on it and click on RUN IN TERMINAL the unpacking starts and after doing it, a message appears saying u need it run it as SUPER USER.
I dont understand as to how to do it. Please help.

---

### Post by baddog144 on 2010-01-17
Open a terminal (Programs -> Accessories -> Terminal), and type
```

gksu nautilus

```
You will be asked for your password. Enter it, and then navigate to the .run file, and do the same thing as before (run in terminal). Hopefully that should work.

---

### Post by anup807 on 2010-01-19
Thank You. It worked...

---

### Post by baddog144 on 2010-01-19
Glad to hear it :)

---

