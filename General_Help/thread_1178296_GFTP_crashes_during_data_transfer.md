---
title: "GFTP crashes during data transfer"
date: 2009-06-04
forum: General Help
---

### Post by fro1269 on 2009-06-04
I have encoutered a recent issue with GFTP with Ubuntu 9.04, when I am transfering large amounts of data, it just crashes on me. From what I read doing a google search on the subject this is a known issue with GFTP. What is a good alternative FTP client you guys can recommend?

---

### Post by jonobr on 2009-06-04
If using windows to Ubuntu, I would try using winscp on the windows box.
Its an easy interface to learn

If using ubuntu to ubuntu,
I would recommend just using command line

it would be something like this to copy a file from place to another

```

scp me@ubuntuaddress:~/myvideos/*.avi .
```

You could also just go places->connect to server
and just use ftp secure ftp or whatever tickles your fancy

---

