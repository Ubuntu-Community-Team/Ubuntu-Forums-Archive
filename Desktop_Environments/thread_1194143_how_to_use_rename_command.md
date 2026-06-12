---
title: "how to use rename command?"
date: 2009-06-22
forum: Desktop Environments
---

### Post by tonjaa on 2009-06-22
if i want to rename file in terminal . it's file .ogg    like   =  desktop-login.ogg
if i want to rename it to name  desktop-009.ogg  how is the correct command ?

---

### Post by milton1 on 2009-06-22
```
mv desktop-login.ogg desktop-009.ogg 
```

---

### Post by mcduck on 2009-06-22
```
mv desktop-login.ogg desktop-009.ogg
```

"mv" as in "move", there's no renaming tool as moving file has the same effect. Execute in the same directory where the files are, or use full paths:

```
mv /path/to/desktop-login.ogg /path/to/desktop-009.ogg
```

---

### Post by tonjaa on 2009-06-22
[COLOR=SeaGreen]Thank you so much for help me.[/COLOR] [COLOR=SandyBrown]for human being [/COLOR]

---

