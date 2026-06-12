---
title: "FTP connection"
date: 2009-06-21
forum: General Help
---

### Post by supravat on 2009-06-21
Hello,
I want to download files from a remote directory from a ftp server. The directory contains multiple files. I want to download all the files in that directory. For this purpose I used the following command
ftp>mget *
but in that case it prompts for every file that is to be downloaded. I just want to off that prompting option, it'll prompt only once.

please some one help me....

---

### Post by smartbei on 2009-06-21
Try this:
```

ftp -h

```
In general programs supply some minimal and useful help documentation when you run the program with one of the following: -h --help
At worst, you can try the man page: man ftp

In case you didn't find it, use "ftp -i" when you start the program, to disable prompting during mget.

---

### Post by supravat on 2009-06-22
thanks

---

### Post by ewankho on 2009-06-22
Or you can try:
ftp>prompt off
To view list of ftp commands:
ftp>help
or 
ftp>help prompt

---

