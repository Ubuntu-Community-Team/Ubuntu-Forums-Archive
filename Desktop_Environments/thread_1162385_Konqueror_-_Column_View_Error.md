---
title: "Konqueror - Column View Error"
date: 2009-05-17
forum: Desktop Environments
---

### Post by maiden30403 on 2009-05-17
Hello,

In Konqueror on Kubuntu 9.04 I get an error saying: "Malformed URL" every time I try to load up something from my file-system, e.g. entering '/' or '~' in the location bar. However this only happens if the view is set to Columns.

Does anyone know what's wrong here?

---

### Post by Kelan on 2009-05-18
Huh, it just started doing this yesterday for me, too.
I think I'd just installed some updates.
I don't know what to do about it though, sorry.

---

### Post by maiden30403 on 2009-05-18
It would appear the error is:

```
Object::connect: No such signal FolderExpander::enterDir(const QModelIndex&)
```

---

### Post by krazyd on 2009-05-18
Can't reproduce here.. 
1. open konq
2. enter '/' in address bar
3. set view mode to columns
4. enter '~' in address bar

all works as expected. anything else I need to do?

---

### Post by maiden30403 on 2009-05-18
Set it to use common views in all folders.
Change the view to columns and close Konqueror.
Now when you open Konqueror and try to browse to the file system it gives this error.

---

### Post by krazyd on 2009-05-18
Hmm. Okay, I'm seeing it now. You can even trigger this just by clicking the reload button in the initial view.
This looks like the bug on kde.org: [http://bugs.kde.org/show_bug.cgi?id=163437](http://bugs.kde.org/show_bug.cgi?id=163437)

Looks like it results from a partially fixed bug a while ago.

---

