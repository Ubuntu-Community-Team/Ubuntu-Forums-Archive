---
title: "file manager permissions"
date: 2009-04-05
forum: General Help
---

### Post by tech666 on 2009-04-05
Hello 
i am a new user of xubuntu and i want to change the skin of alvaro's messanger .after some time i become ,with an my action of the terminal,i become the rrot of my computer but the problem is the same : i can't change the permission of the folder "filesystem" to insert a new skin .
someone can help me? 
thanks in advance 
tech666

---

### Post by zigga15 on 2009-04-05
> **tech666 said:**
> Hello 
i am a new user of xubuntu and i want to change the skin of alvaro's messanger .after some time i become ,with an my action of the terminal,i become the rrot of my computer but the problem is the same : i can't change the permission of the folder "filesystem" to insert a new skin .
someone can help me? 
thanks in advance 
tech666

To view the permissions of a folder

ls -lt {folder_name}

to change the permissions:

chmod
Run man chmod for more details. Or if you want to be nasty just run chmod -R 777 {filename}

---

### Post by ajgreeny on 2009-04-05
Or you can start the file-manager with ```
gksudo thunar
``` and just move the files you want into the folder you want.  Be careful and close thunar as soon as possible, or you could do a lot of harm.  **Don't** change the permissions of system folders or you could find yourself unable to boot up at all.

---

