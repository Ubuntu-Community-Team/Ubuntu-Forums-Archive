---
title: "How to add MySQL to my path?"
date: 2009-06-11
forum: General Help
---

### Post by LambertDan on 2009-06-11
Hi,

I installed XAMPP For Linux and need to add MySQL to my shell path I know I can do that Export to Path command but that only works until I close the Terminal. How do I make it stay permanently?

---

### Post by LambertDan on 2009-06-13
Can anyone help?

---

### Post by spiderbatdad on 2009-06-13
edit .bashrc
```
export PATH=$PATH:<path>
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:<path>
```

---

### Post by LambertDan on 2009-06-14
> **spiderbatdad said:**
> edit .bashrc
```
export PATH=$PATH:<path>
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:<path>
```

Thanks :)

---

