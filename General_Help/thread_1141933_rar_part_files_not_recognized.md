---
title: "rar part files not recognized"
date: 2009-04-28
forum: General Help
---

### Post by zero777zero on 2009-04-28
[IMG]http://i41.tinypic.com/ej61qq.png[/IMG]

when i click on the first file and unrar it i get the following error: 

Dj set.flac - CRC failed
Unexpected end of archive

---

### Post by taurus on 2009-04-28
What happens if you run it from a terminal.  Make sure you are in the directory where those files are located first.

```
unrar x sits.rar.001
```

p.s.  You need to install unrar first if it's not on your system.

---

### Post by zero777zero on 2009-04-28
i already have the rar stuff installed from add/remove

heres my output:

Dj set.flac - CRC failed
Unexpected end of archive
Total errors: 2

---

### Post by michy99 on 2009-04-28
This is one RAR file which has been split using HJSLPIT or a similar program. You can put it back together with the cat command.

Open a terminal and change to the directory containing the files.

Enter ```
cat sits.rar.* > sits.rar
```

Now extract sits.rar.

---

### Post by zero777zero on 2009-04-28
success

thanks :razz:

---

### Post by constantmin on 2012-02-09
Hi! 

I have a similar problem, so i thought of posting it here.

I get the same exact error message, but i cannot apply what [SIZE="3"]michy99[/SIZE] because the file.rar.r00 etc are already in a rar file. 
So, i cannot unrar them because it says "Unexpected end of archive" 
and i cannot use the cat command in the rar.* files because they are inside the rar. 

Can anyone help? 
Thanks in advance

---

### Post by raja.genupula on 2012-02-09
it always better start your own thread for good solutions .so please make your own thread .

---

### Post by constantmin on 2012-02-09
Sorry 
and thanks :p

---

### Post by oldos2er on 2012-02-09
Closed, necromancy.

---

