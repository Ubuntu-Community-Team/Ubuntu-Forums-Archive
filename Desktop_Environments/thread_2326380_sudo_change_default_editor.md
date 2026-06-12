---
title: "sudo change default editor"
date: 2016-05-31
forum: Desktop Environments
---

### Post by james226 on 2016-05-31
ok i set the EDITOR variable to vi when i use the command "visudo" as a root user im in vi mode like expected
but when i use the command "sudo visudo" even with the root user i got back to nano editor why?
i set the EDITOR variable in the "regular" user as well.
p.s
im using lubuntu 16.04

---

### Post by CantankRus on 2016-05-31
Have a look at 
```
man visudo
```

What does alternatives tell you...
```
sudo update-alternatives --config editor
```

---

