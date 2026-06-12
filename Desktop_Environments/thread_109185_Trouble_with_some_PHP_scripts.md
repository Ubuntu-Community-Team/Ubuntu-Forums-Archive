---
title: "Trouble with some PHP scripts"
date: 2005-12-28
forum: Desktop Environments
---

### Post by three_sixteen on 2005-12-28
I'm trying to use some of the PHP scripts I've written while I used windows, but am running into permission problems when I try to run them.

I understand from my previous experience with unix that I need to give apache permission to run as a priviledged user so that it can open, read and write files, but I don't know how to do that.

---

### Post by Corvillus on 2005-12-28
The easiest way to go about this is to probably give apache ownership of the file that you want php to have write access to. You can do this with
```
sudo chown www-data:www-data <filename>
```

---

### Post by paddyg on 2005-12-28
PHP scripts are usually chmod 644 (world-readable)

---

