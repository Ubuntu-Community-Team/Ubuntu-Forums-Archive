---
title: "Symbolic linking directories???"
date: 2008-12-29
forum: General Help
---

### Post by jondecker76 on 2008-12-29
I am trying to make it so that the evolution addressbook is the same accross multiple users by putting the data files in a shared area, and replacing the original data files in the user's home directories with symbolic links to the master data file in a shared area..  However, when I try to create a symbolic link, i get an error that I can't link a directory... Any idea how I should be approaching this?


```

traceydecker82@studio-desktop:~/.evolution$ ln /home/share/.evolution/addressbook addressbook
ln: `/home/share/.evolution/addressbook': hard link not allowed for directory
traceydecker82@studio-desktop:~/.evolution$ 



```

---

### Post by wmoore on 2008-12-29
Try:```
ln -s /home/share/.evolution/addressbook
```

---

### Post by cdtech on 2008-12-29
You have to use the -d flag. See "man ln" for more information:
> -d, -F, --directory
allow the superuser to attempt to hard link  directories  (note:will probably fail due to system restrictions, even for the superuser)

**UPDATE::.**
My bad, you just need to create the symlink for the address book. I mis read the post....

---

### Post by ajcham on 2008-12-29
> **jondecker76 said:**
> 
```

traceydecker82@studio-desktop:~/.evolution$ ln /home/share/.evolution/addressbook addressbook
ln: `/home/share/.evolution/addressbook': hard link not allowed for directory
traceydecker82@studio-desktop:~/.evolution$ 


```

You need to use the **-s** option with **ln**.  **ln** on it's own tries to create a hard link, whereas the **-s** option tells it to create a symbolic link.
```

ln -s /home/share/.evolution/addressbook addressbook

```

---

