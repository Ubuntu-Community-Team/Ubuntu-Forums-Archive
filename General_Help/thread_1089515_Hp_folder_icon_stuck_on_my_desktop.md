---
title: "Hp folder icon stuck on my desktop"
date: 2009-03-07
forum: General Help
---

### Post by redb on 2009-03-07
I downloaded the drivers for hp printers to my desktop and set up the program from a deb file.  The printer works great but the icon has an X and a lock showing up on it.  I cant get rid of it.  What did I do wrong and how can I get rid of it?

Mike

---

### Post by Hobgoblin on 2009-03-07
Right click > properties > permissions

Are you owner and do you have write access?

---

### Post by Scar-face on 2009-03-07
I'm guessing you downloaded it as root.
startup a terminal
execute this
```
sudo rm -d -r *nameofdownloadedfolder*
```

---

### Post by redb on 2009-03-07
> **Scar-face said:**
> I'm guessing you downloaded it as root.
startup a terminal
execute this
```
sudo rm -d -r *nameofdownloadedfolder*
```


That worked!  Thank you very much:)

---

