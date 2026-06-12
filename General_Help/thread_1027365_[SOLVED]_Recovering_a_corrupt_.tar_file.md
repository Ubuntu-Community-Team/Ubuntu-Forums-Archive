---
title: "[SOLVED] Recovering a corrupt .tar file"
date: 2009-01-01
forum: General Help
---

### Post by Sevis on 2009-01-01
Good day,

Recently, I needed to make a backup of some data before installing ubuntu on a computer. I could only use my USB for that purpose, and so archived the files into a .tar in order for it to fit (the result was 1.9 GB). I used the LiveCD archiver. However, when I try to open it now it gives an error:

```

(null)

tar: Skipping to next header
tar: Error exit delayed from previous errors
```

I am using the default archiver (fileroller?)

The tar: lines are in the details, the (null) is shown.

Is it possible to fix this archive?

Thank you,
Sevis

---

### Post by cmnorton on 2009-01-01
Will tar list this file?

tar -xtf corrupt-tar-file

---

### Post by Sevis on 2009-01-01
```
katherine@katherine-desktop:~$ tar -xtf /media/disk/bak.tar 
tar: You may not specify more than one `-Acdtrux' option
Try `tar --help' or `tar --usage' for more information.

```

Edited into English.

EDIT:

I removed the x and it lists the folders and files inside.

---

### Post by cmnorton on 2009-01-01
Mea culpa. You cannot combine extract with list. 

Just use t, instead of x. 

tar -tvf corrupt-tar-file

---

### Post by Sevis on 2009-01-01
Yes, it lists a lot of files... It\'s too much to list here.

For example:

```
-rwxrwxrwx root/root    401282 2008-03-31 11:20 Disc_D/&#1050;&#1080;&#1090;&#1072;&#1081; - &#1089;&#1074;&#1086;&#1076;&#1085;&#1072;&#1103; &#1075;&#1072;&#1083;&#1077;&#1088;&#1077;&#1103;/080313-165730-618ma.jpg
```

---

### Post by cmnorton on 2009-01-01
Then tar should be able to unpack this file for you.

tar -xvf corrupt-tar-file

---

### Post by Sevis on 2009-01-02
Yes, that worked, thank you! :D

---

