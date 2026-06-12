---
title: "Drag 'n' Drop files - no permission"
date: 2006-01-14
forum: Desktop Environments
---

### Post by Autolycus on 2006-01-14
I am trying to copy a file (via the Drag and Drop method) and I get a "do not have permission to do" that message..

The file to be moved is in /user/bin and I want to go to a folder within a folder on the desktop...

TIA...

---

### Post by jeffreyvergara.NET on 2006-01-14
try in terminal:
"sudo nautilus"

then input your password. You can now cut & paste anywhere, just like in Window$... ^^

---

### Post by aysiu on 2006-01-14
[QUOTE=jeffreyvergara.NET]try in terminal:
"sudo nautilus"

then input your password. You can now cut & paste anywhere, just like in Window$... ^^[/QUOTE] Or Alt-F2 and ```
gksudo nautilus
```

---

### Post by icarius on 2006-01-14
open the terminal and cd the folder you want to drag and drop, then type chmod 770 */*   which should give you permission to do whatever you want to the folder, and if that doesn't work, try 777. Let me know how it works, oh, and you hve to do this as the superuser


Prince Icarius

---

### Post by Autolycus on 2006-01-14
ALT-F2
gksudo nautilus

did the trick


thanks so much...

---

