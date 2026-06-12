---
title: "Blank divider in GRUB"
date: 2009-06-06
forum: General Help
---

### Post by solidsnake204 on 2009-06-06
Is there any way to have a blank divider without it hiding the options below?

Thanks in advance.

---

### Post by Legace on 2009-06-06
This will create a blank entry:

```
title		
root
```

---

### Post by solidsnake204 on 2009-06-06
I knew using a character would not hide items below it, I wanted to know if it was possible to have it blank.

Thanks anyway.


Perhapps if I put many spaces before a -, the - will be off screen? Or will it go to the next line?

---

### Post by Legace on 2009-06-06
I tested it completely blank, and it works:
```
title		
root
```

---

