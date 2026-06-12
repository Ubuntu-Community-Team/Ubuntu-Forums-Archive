---
title: "Trash error"
date: 2006-07-16
forum: Desktop Environments
---

### Post by Owdy on 2006-07-16
Every time i empty trash, it gives error ' cant remove some file because dont have permissions to upper folder'. Trash is empty, no hidden files. Roots trash is empty also. Whats happening?

---

### Post by philippe_carlo on 2006-07-16
Are you sure you own the ~/.Trash directory? If you do ls -al ~/.Trash, what do you get? Are there files owned by root or other user(s)?

---

### Post by Owdy on 2006-07-16
```
osku@koti:~/.Trash$ ls -al ~/.Trash
yhteensä 120
drwx------  3 osku osku   4096 2006-07-16 11:52 .
drwxr-xr-x 73 osku osku   4096 2006-07-16 11:51 ..
drwxr-xr-x  2 osku osku   4096 2006-07-16 11:51 img
-rw-r--r--  1 osku osku    500 2006-07-16 11:51 index.html
-rw-r--r--  1 osku osku 102067 2006-07-16 11:51 template_thumbnail14.png
```

---

### Post by Owdy on 2006-07-16
Weird. If i move test.png to trash and empty trash, its says 'cant remove test.png etc'. Still it removes that file. I dont get this.

---

### Post by Owdy on 2006-07-16
Even weirder. This wont give any errors```
 rm -r ~/.Trash/*
``` . So this is some nautilus bug.

---

### Post by Anduu on 2006-07-16
Open your trash and do a Ctrl+H....I bet there is a hidden file in there that you don't have permission to write.

---

### Post by Owdy on 2006-07-16
There arent any hidden files.

---

### Post by LordofHaha on 2006-07-16
have you tried making your trash folder chmod 777? 

cmd be something like:

sudo chmod 777 -r ~/.Trash

---

### Post by Owdy on 2006-07-16
Yes i have.

---

### Post by Owdy on 2006-08-15
Sorry but *bump*

---

### Post by Owdy on 2006-08-29
:confused:

---

