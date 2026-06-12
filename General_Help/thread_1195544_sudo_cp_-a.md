---
title: "sudo cp -a"
date: 2009-06-23
forum: General Help
---

### Post by Muscovy on 2009-06-23
I'm trying to customize a cd, but upon the command 
```

sudo cp -a squashfs/* edit/

```
the system just doesn't seem to respond. I'm assuming that it's just my computer lagging out. What does the command mean? Is there any way I can carry it out in GUI?

---

### Post by bjk03 on 2009-06-23
do a man cp in the terminal to see what -a means.

---

### Post by Muscovy on 2009-06-24
The cp -a copies and archieves. This would, I assume, put everything in the file squashfs and archieve it in a directory called edit?
  Well, I'm assuming I can still do it through terminal, as archieving something that large does take a while.

---

### Post by michy99 on 2009-06-24
If you add the verbose switch -v it will tell you what it is doing.```
sudo cp -av squashfs/* edit/
```

---

### Post by Polaris96 on 2009-06-24
try adding -r 

If all else fails, you can copy anything with dd

---

### Post by colau on 2009-06-24
> **Muscovy said:**
> I'm trying to customize a cd, but upon the command 
```

sudo cp -a squashfs/* edit/

```
the system just doesn't seem to respond. I'm assuming that it's just my computer lagging out. What does the command mean? Is there any way I can carry it out in GUI?
This command will copy everything of squashfs directory to edit directory.
But if there is any directory/folder inside the squashfs. thas command will not copy that directory/folder to edit directory.

-a option for archive mode

See
```

man cp

```

---

