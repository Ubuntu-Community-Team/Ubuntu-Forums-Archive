---
title: "ls via ssh"
date: 2009-01-28
forum: General Help
---

### Post by any.linux12 on 2009-01-28
Is possible to ls a directory in other computer like:
ls ssh://admin@192.168.1.100/home/admin

I thought this was the right syntax but...does not work 
"No such file or directory"

Thanks in advance

---

### Post by geirha on 2009-01-28
This should work better:
```
ssh admin@192.168.1.100 "ls /home/admin"
```

---

### Post by any.linux12 on 2009-01-28
Very nice :D

Thanks

---

