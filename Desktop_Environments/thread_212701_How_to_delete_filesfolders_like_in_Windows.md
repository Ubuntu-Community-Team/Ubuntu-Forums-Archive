---
title: "How to delete files/folders like in Windows?"
date: 2006-07-10
forum: Desktop Environments
---

### Post by Don_DiZzLe on 2006-07-10
Hello,

Is there a way to delete files/folders just like in Windows by selecting them and delete.

The current method I use is with the sudo rm (-rf) command, but as u can see the files that I wanna delete are scattered all over the place.

---

### Post by kb3hkg on 2006-07-10
absolutely, just open up your file manager and go into the directories thrugh the rphical interface.

---

### Post by Don_DiZzLe on 2006-07-10
First thing I did obviously but there that whole premission problem that;s preventing the deletion.

---

### Post by lordlollo on 2006-07-10
If in the text mode you use sudo, in the same way you must use gksudo in the graphical mode

```
gksudo nautilus
```

Now you can delete what you want... Pay attention... ;) 

Cheers.

---

### Post by Don_DiZzLe on 2006-07-10
Thnx dude, that worked like a charm!

---

