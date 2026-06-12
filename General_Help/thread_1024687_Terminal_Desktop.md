---
title: "Terminal /Desktop"
date: 2008-12-29
forum: General Help
---

### Post by gm__ on 2008-12-29
Hi!

Id like to know if there is a way to be in the desktop directly when i open it.
I have a terminal shortcut on the desktop but when i open it, it opens in another folder 
not like windows's cmd that navigates in the folder where you put cmd.

Thanks in advance!

---

### Post by wizard10000 on 2008-12-29
> **gm__ said:**
> Hi!

Id like to know if there is a way to be in the desktop directly when i open it.
I have a terminal shortcut on the desktop but when i open it, it opens in another folder 
not like windows's cmd that navigates in the folder where you put cmd.

Use this command line for your launcher -

```
gnome-terminal --working-directory=/home/*username*/Desktop
```

---

### Post by Dr Small on 2008-12-29
Open ~/.bashrc and append this line to the bottom of it:
```
cd Desktop/
```

---

### Post by gm__ on 2008-12-29
Great!  :D    Thanks to both of you!

---

