---
title: "Files in shared directory won't open with double-click"
date: 2006-07-14
forum: Desktop Environments
---

### Post by vayu on 2006-07-14
I have some shared directories mounted using smbfs.  When I try to double click to open a file in those directories they won't just open.  I have to right-click and choose "open with".

I get the below error message: (normally php files will open in gedit)
How can I turn this security setting off?

```
The filename "index.php" indicates that this file is of type "PHP script". The contents of the file indicate that the file is of type "HTML document". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "HTML document", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file. 
```

---

### Post by mssever on 2006-07-14
Nautilus determines the file type by trying to guess the mimetype instead of using the extention. In the case of PHP files, it often fails miserably. Im my opinion, this is a braindead behavior. It should rely on the extension and fall back to mimetype guessing only for tiles with no extension or an unknown extension. As far as I know, there's no way to change this. :( 

Hopefully I'm wrong?

---

### Post by Swab on 2006-07-14
> **mssever said:**
>  As far as I know, there's no way to change this. :( 

Hopefully I'm wrong?

Hmmm... can't find any way with gconf-editor...

---

