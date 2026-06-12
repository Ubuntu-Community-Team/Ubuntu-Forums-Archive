---
title: "Need to delete corupt file"
date: 2009-03-30
forum: General Help
---

### Post by measekite on 2009-03-30
On a drive formatted for ntfs I have a corupt db file that I must delete.  I cannot delete it.  

I even booted Windows and tried to delete it from there.  I got a message that said "cannot delete file is corupt"

How can you delete this file?

---

### Post by jocheem67 on 2009-03-30
The "rm" command doesn't work, even as root?

---

### Post by blazemore on 2009-03-30
yeah 
```
 sudo rm -fv /path/to/**file**
```

Be careful!

---

### Post by measekite on 2009-03-30
> **jocheem67 said:**
> The "rm" command doesn't work, even as root?


nothing seems to work.  I even, as I said, tried to do it in windows.  When I rt clicked and chose delete in nautilus it disappeared but when I brought nautilus up and down it was back.

I have not had any problems with ext3, just a few issues with ntfs.

In the next few months ext4 will be out and who knows how that will be.

---

### Post by measekite on 2009-03-30
> **blazemore said:**
> yeah 
```
 sudo rm -fv /path/to/**file**
```Be careful!

what does -fv do?

---

### Post by change_mode on 2009-03-30
> **measekite said:**
> what does -fv do?


--force --verbose

(man rm)

Did you try the windows safe mode?

---

### Post by measekite on 2009-03-30
> **change_mode said:**
> --force --verbose

(man rm)

Did you try the windows safe mode?

Here is how I solved the problem.

Booted Windows
Ran CheckDisk /f
   found and fixed a bunch of bad segments
Deleted the bad corrupt file
Ran DeFrag
  really did not need to but it did improve performance unexpectedly
ShutDown Windows
Booted Linux

This was an ntfs drive so I felt better using chkcsk /f in Windows instead of fsck -v in Linux.

Thanks for your help but it appears I had two issues.  Corrupt DB Journal and bad segments somewhere

---

