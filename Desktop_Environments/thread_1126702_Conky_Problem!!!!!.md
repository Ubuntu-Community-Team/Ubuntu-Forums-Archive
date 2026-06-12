---
title: "Conky Problem!!!!!"
date: 2009-04-15
forum: Desktop Environments
---

### Post by nathanpc on 2009-04-15
Hello,
 When i start Conky with the double buffer(that prevents conky to flash), my desktop disapear.

Help Me Please,
 Nathan Paulino Campos

---

### Post by Sarai the Geek on 2009-04-15
Make sure this is included in the upper portion of your conkyrc:

```
own_window yes 
own_window_transparent yes 
own_window_type override 
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
```

---

### Post by nathanpc on 2009-04-15
Thanks.
Good Blog!

Thanks soo Much,
 Nathan Paulino Campos

---

### Post by Sarai the Geek on 2009-04-15
> **nathanpc said:**
> Thanks.
Good Blog!

Thanks soo Much,
 Nathan Paulino Campos

'Tis my pleasure!

---

