---
title: "No more free space"
date: 2009-04-10
forum: General Help
---

### Post by Lino90 on 2009-04-10
My problem:
I tried to do a buckup's copy of my ubuntu. I used the command "sudo tar.." and it made a file, called "backup.tar", of 4GB. Anyway the free space of my HD was 0, so I decided to delete the backup's file.
The file is deleted, but I can't find it in my Wastebasket and the free space is still 0.
What's the matter?

(my english is not very good:p)

---

### Post by utnubuuser on 2009-04-10
Hi -- Try View>>Show hidden files in your file-browser

---

### Post by Elfy on 2009-04-10
It is likely that it is in roots trash if you used sudo to create the tar - check that too

[http://ubuntuforums.org/showpost.php?p=5649417&postcount=1](http://ubuntuforums.org/showpost.php?p=5649417&postcount=1)

---

### Post by Lino90 on 2009-04-11
Thank's!
I've found the file in "root/.local/share/Trash/files/"
with ```
 sudo find / -size +500M
```

---

