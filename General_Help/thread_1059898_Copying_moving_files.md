---
title: "Copying moving files"
date: 2009-02-04
forum: General Help
---

### Post by nemiux on 2009-02-04
I installed xampp, and now i need to edit files, it is in opt, cause it must be installed in there, but i cant access that directory. So how i move or copy files from terminal, or how do i move, copy, edit files in opt directory?

Thanks

---

### Post by howefield on 2009-02-04
Start nautilus with admin rights, in terminal type

```
gksu nautilus
```

Goes without saying, be careful. :D

---

### Post by Neural oD on 2009-02-04
on the command line you could always use the mv command - this will move or rename files - you can also use it with the sudo command - in case of permissions issues - use carefully though - there is a flag - check the man pages - that will prompt you for each mv

---

### Post by nemiux on 2009-02-04
Thanks, my problem is sloved

---

