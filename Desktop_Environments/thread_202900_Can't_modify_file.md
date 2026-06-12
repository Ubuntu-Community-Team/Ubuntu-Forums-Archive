---
title: "Can't modify file"
date: 2006-06-24
forum: Desktop Environments
---

### Post by linux_student_user on 2006-06-24
I would like to modify the following file but cant seem to save any changes to it 

/usr/share/icons/default.kde/16x16/apps/Kmenu.png - I am the only user and im sure I must have admistrator rights, any ideas? 

Thanks.

Mike

---

### Post by Winblowz on 2006-06-24
Since it sounds like you're using KDE, open Konqueror as root and then try to save the file.

---

### Post by lamego on 2006-06-24
With Ubuntu you are not an administrator, you are just a regular user.
If you need to do something that requires administration privileges you will need to use a specific command and the password for it.
Save the file into your home dir, then copy it with admin privileges (using sudo).
Using the terminal:
```
sudo cp file.png /system/path/
```

---

