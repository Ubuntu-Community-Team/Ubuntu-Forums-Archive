---
title: "Which program to create archives through the terminal?"
date: 2005-12-26
forum: Desktop Environments
---

### Post by GabrielWolff on 2005-12-26
The title sums it up: I am looking for a program to create archives using the console. Unrar, as far as I understand it, only unrars.

Thanx

Gabriel

---

### Post by arpunk on 2005-12-26
zip, tar, bzip2, gzip?

---

### Post by GabrielWolff on 2005-12-26
[QUOTE=arpunk]zip, tar, bzip2, gzip?[/QUOTE]

OK...

...to create .rar archives?

Gabriel

---

### Post by pharcyde on 2005-12-26
Try this

> 
sudo apt-get install rar

rar a <archive.rar> <file list>


You could always "man rar" and see the extended syntax

---

### Post by kaamos on 2005-12-26
rar? :)

For example to create an archive "archive.rar" and add a file to it:
```
rar a archive.rar textfile.txt
```

---

