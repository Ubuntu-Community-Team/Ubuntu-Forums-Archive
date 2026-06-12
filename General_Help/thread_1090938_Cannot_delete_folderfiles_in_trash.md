---
title: "Cannot delete folder/files in trash"
date: 2009-03-08
forum: General Help
---

### Post by arvadawest on 2009-03-08
Good day,

I was emptying my trash folder and notices that 1 folder and 4 files would not delete from the trash folder.  I checked persmissions and what was interesting is that Ubuntu will not allow me to change permissions to this folder/files in the trash area and yet I am logged on as admin. First time I couldn't remove what is in the trash folder.  Never have seen this before.  Has anyone had this problem before and how did you solve it?  Thank you.  -aw

---

### Post by taurus on 2009-03-08
What's the output of this command from a terminal?

```
ls -la ~/.local/share/Trash/files
```

---

