---
title: "Open Office 3.0 Issues"
date: 2009-04-23
forum: General Help
---

### Post by wdbreen on 2009-04-23
Gday Guys,
Just upgraded to jaunty last night and all went well.
Tried to edit an open office calc file and found i couldnt save it.  It came up with a write error: the file could not be written.
The file is being read from a usb drive but it is also happening if i copy the same file to my home directory, open it, edit it and then attempt to save it again.
The application (OOo) will open and save a file that was already on the home directory. Hmmm....
Any thoughts??

---

### Post by snowpine on 2009-04-23
File->Save As
Save a copy to your home directory.

---

### Post by wdbreen on 2009-04-23
> **snowpine said:**
> File->Save As
Save a copy to your home directory.
That doesnt work either. Same error occurs but thanks.

---

### Post by Peter09 on 2009-04-23
Check permissions on the files in your directory.

```
ls -alg
```

---

