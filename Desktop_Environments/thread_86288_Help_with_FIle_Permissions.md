---
title: "Help with FIle Permissions"
date: 2005-11-04
forum: Desktop Environments
---

### Post by Georgie-o on 2005-11-04
If I want to save an entire folder full of pictures to a CD, how do I make it readable by anyone without changing the permissions for _each_ picture _individually_?


Thanks

---

### Post by cwaldbieser on 2005-11-04
[QUOTE=Georgie-o]If I want to save an entire folder full of pictures to a CD, how do I make it readable by anyone without changing the permissions for _each_ picture _individually_?


Thanks[/QUOTE]
From the terminal:
```

$ chmod -R path_to_folder

```
will change the permissions recursively.  I think there is a checkbox in Nautilus you can use to do this.  I know there is one in the file permissions dialog in Konqueror.

---

