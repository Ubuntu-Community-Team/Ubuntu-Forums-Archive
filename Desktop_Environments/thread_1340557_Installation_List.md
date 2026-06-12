---
title: "Installation List"
date: 2009-11-28
forum: Desktop Environments
---

### Post by kiran88pnjr on 2009-11-28
I want to get a list of installed softwares (packages) in my Ubuntu.
How can I do that ?

---

### Post by billyboy1978 on 2009-11-28
$ man dpkg

$ dpkg --get-selections

---

### Post by sisco311 on 2009-11-28
Open a terminal (Application -> Accessories -> Terminal)
and paste:
```
dpkg --get-selections | awk '$2=="install"{print $1}' > ~/Desktop/installed.txt
```

the command will create a file (installed.txt) on your Desktop with the list of the installed packages.

---

### Post by kiran88pnjr on 2009-11-28
> **billyboy1978 said:**
> $ man dpkg

$ dpkg --get-selections

Whether I need to install any packages to do that ?

---

### Post by billyboy1978 on 2009-11-28
no :) This give you a list of installed apps in the terminal.

go for sisco311's command, this store given info into a file..

---

### Post by kiran88pnjr on 2009-11-28
> **sisco311 said:**
> Open a terminal (Application -> Accessories -> Terminal)
and paste:
```
dpkg --get-selections | awk '$2=="install"{print $1}' > ~/Desktop/installed.txt
```

the command will create a file (installed.txt) on your Desktop with the list of the installed packages.

Thanks man ! I've it.

:p:p:p:p:p

---

### Post by kiran88pnjr on 2009-11-28
> **billyboy1978 said:**
> no :) This give you a list of installed apps in the terminal.

go for sisco311's command, this store given info into a file..

Thanks. I've it.
:p:p:p:p

---

