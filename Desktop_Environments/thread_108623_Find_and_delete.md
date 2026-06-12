---
title: "Find and delete"
date: 2005-12-26
forum: Desktop Environments
---

### Post by harisund on 2005-12-26
The other day, I was moving all the files from my Windows box to my Linux file server. However, in Windows there is a hidden file called "Thumbs.db" which gets created when I enable thumbnail view.

Now I do not want those in my Linux box. I did
sudo find /home/hari -name Thumbs.db

And it gave me a complete listing. Now how do I remove each one of those? 

Thanks !!

---

### Post by kabus on 2005-12-26
This should remove Thumbs.db in the curent directory and its subdirectories :

```
find . -name Thumbs.db -exec rm -i '{}' \;
```

(I added the -i switch so it won't delete anything without confirmation in case I made an error.)

---

### Post by harisund on 2005-12-26
Thanks for that command.. could you give me some help on what exactly the exec function does?

---

### Post by kabus on 2005-12-26
It executes a command, rm in this case, on the files that match your search. 
The {} represent the current file.

You can read about it in more detail in the find manpage.

---

