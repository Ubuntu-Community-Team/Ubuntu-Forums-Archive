---
title: "cant share files"
date: 2008-12-09
forum: General Help
---

### Post by mscout2004 on 2008-12-09
When I try to share a folder, it downloaded some files and installed the sharing ability. When I go into the sharing options of a folder inside my home folder, it says that it can not do it as it can't open the /var/lib/samba/usershares folder. I went to that folder and it says I can't access the folder as I don't own it. It says the owner is "root". How do I login as "root" or gain those abilities in my user to edit that folder to be able to share folders???

THANKS For The Help,
New Ubuntu User

---

### Post by Iowan on 2008-12-09
> **mscout2004 said:**
>  How do I login as "root" or gain those abilities in my user to edit that folder to be able to share folders???
Precede the command with **sudo** - or, if you're using a graphical editor like gedit, use **gksudo**. That's the answer to the question - but may not solve the problem...

---

### Post by spiderbatdad on 2008-12-09
open a terminal...Applications>>Accessories>>Terminal
type: ```
gksu nautilus
```now navigate to the folder you want to share and right click to select sharing. Be careful using nautilus as root...that is; don't go open all kinds of system files as root. Accidentally deleting a letter in a file could cause you problems.

---

### Post by mscout2004 on 2008-12-09
i tryed using that command in the terminal and it said it could not open display.  ?????

---

### Post by spiderbatdad on 2008-12-09
are you using the admin user account?

---

